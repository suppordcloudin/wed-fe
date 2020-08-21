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
                @click="delConf()"
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
          sortable: true,
        },
        {
          key: "phone",
          sortable: false,
        },
        {
          key: "attend",
          label: "Kehadiran",
          sortable: true,
        },
        { key: "actions", label: "Actions" },
      ],
      items: [
        { phone: 21, name: "Larsen", wish: "dsadsadsa", attend: "Yes" },
        { phone: 89, name: "Geneva", wish: "dsadsadsa", attend: "No" },
        { phone: 38, name: "Jami", wish: "dsadsadsa", attend: "Yes" },
      ],
      backup: [],
    };
  },
  created() {
    this.backup = this.items;
    this.auth = localStorage.getItem("auth");

    if (this.auth != "login") {
      this.$router.push({ name: "Login" });
    }
  },
  methods: {
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
    delConf() {
      this.conf();
    },
    conf() {
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
          console.log("file berhasil dihapus!");
          location.reload();
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
