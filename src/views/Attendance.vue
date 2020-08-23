<template>
  <div class="containerz">
    <b-row>
      <b-col cols="12 text-center pb-3">
        <b-button-group>
          <b-button
            variant="secondary"
            size="sm"
            @click="showAllList()"
            class="mr-1"
          >
            List Semua Kehadiran
          </b-button>
          <b-button
            variant="secondary"
            size="sm"
            @click="showAttend()"
            class="mr-1"
          >
            List Datang
          </b-button>
          <b-button
            variant="secondary"
            size="sm"
            @click="showNotAttend()"
            class="mr-1"
          >
            List Tidak Datang
          </b-button>
        </b-button-group>
      </b-col>
      <b-col cols="12">
        <b-table
          small
          striped
          hover
          :items="items"
          :fields="fields"
          responsive="sm"
        >
          <template v-slot:cell(index)="data">
            {{ data.index + 1 }}
          </template>

          <template v-slot:cell(actions)="row">
            <b-button-group>
              <b-button
                variant="danger"
                size="sm"
                @click="delConf(row.index)"
                class="mr-1"
              >
                Delete
              </b-button>
              <b-button
                variant="secondary"
                size="sm"
                @click="showWish(row.index)"
                class="mr-1"
              >
                Show Wish
              </b-button>
            </b-button-group>
          </template>
        </b-table>
      </b-col>
    </b-row>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      auth: false,
      fields: [
        {
          key: "index",
          label: "Nomor",
        },
        {
          key: "name",
          sortable: false,
        },
        {
          key: "phone",
          sortable: false,
        },
        {
          key: "attend",
          label: "Kehadiran",
          sortable: false,
        },
        { key: "actions", label: "Actions" },
      ],
      items: [],
      backup: [],
      url:
        "https://zu8bjg7t2f.execute-api.us-east-1.amazonaws.com/dev/api/wedding/users",
    };
  },
  created() {
    this.getData();
    this.auth = localStorage.getItem("auth");

    if (this.auth != "login") {
      this.$router.push({ name: "Login" });
    }
  },
  methods: {
    getData() {
      return new Promise((resolve, reject) => {
        axios
          .get(this.url)
          .then((response) => {
            console.log(response.data);
            this.items = response.data;
            this.backup = this.items;
          })
          .catch((e) => {
            reject(e);
            this.getData();
          });
      });
    },
    removeData(idnya) {
      return new Promise((resolve, reject) => {
        axios
          .delete(this.url + "/" + idnya)
          .then((response) => {
            this.hapusSukses();
          })
          .catch((e) => {
            reject(e);
          });
      });
    },
    remove(index) {
      alert(this.items[index].name);
    },
    showWish(index) {
      this.show(this.items[index].wish);
    },
    showAllList() {
      this.items = this.backup;
    },
    showAttend() {
      this.items = [];
      this.backup.forEach((col) => {
        if (col.attend == "Yes") {
          this.items.push(col);
        }
      });
    },
    showNotAttend() {
      this.items = [];
      this.backup.forEach((col) => {
        if (col.attend == "No") {
          this.items.push(col);
        }
      });
    },
    show(val) {
      this.$swal({
        text: val,
        confirmButtonColor: "#3085d6",
        confirmButtonText: "Back",
      });
    },
    hapusSukses() {
      this.$swal({
        icon: "success",
        title: "Berhasil menghapus data",
        confirmButtonColor: "#3085d6",
        confirmButtonText: "unch",
      }).then((result) => {
        location.reload();
      });
    },
    delConf(index) {
      this.$swal({
        title: "Are you sure?",
        text: "You won't be able to revert this!",
        icon: "warning",
        showCancelButton: true,
        confirmButtonColor: "#3085d6",
        cancelButtonColor: "#d33",
        confirmButtonText: "Yuhu",
      }).then((result) => {
        if (result.value == true) {
          this.removeData(this.items[index]._id);
        }
      });
    },
  },
};
</script>

<style scoped>
.containerz {
  height: auto;
  width: 100%;
}
</style>
