<template>
  <div class="containerz">
    <b-row>
      <b-col cols="12 text-center pb-3">
        <b-button-group>
          <b-button
            variant="secondary"
            size="sm"
            @click="info(row.index)"
            class="mr-1"
          >
            List Semua Kehadiran
          </b-button>
          <b-button
            variant="secondary"
            size="sm"
            @click="info(row.index)"
            class="mr-1"
          >
            List Datang
          </b-button>
          <b-button
            variant="secondary"
            size="sm"
            @click="info(row.index)"
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
                @click="remove(row.index)"
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
      // Note 'isActive' is left out and will not appear in the rendered table
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
  },
  methods: {
    remove(index) {
      alert(this.items[index].name);
    },
    showWish(index) {
      alert(this.items[index].wish);
    },
    showAllList() {},
    showAttend() {},
    showNotAttend() {},
  },
};
</script>

<style scoped>
.containerz {
  height: auto;
  width: 100%;
}
</style>
