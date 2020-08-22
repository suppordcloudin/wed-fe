<template>
  <div class="content2">
    <div class="bg">
      <b-container class="bv-example-row text-center">
        <b-row>
          <b-col cols="12 title"
            >Att<label style="border-bottom: 2px solid white;">enda</label
            >nce</b-col
          >
          <b-col cols="12 pb-3">
            <b-form-input
              v-model="name"
              placeholder="enter your name here"
            ></b-form-input>
          </b-col>
          <b-col cols="12 pb-3">
            <b-form-input
              v-model="phone"
              placeholder="enter your phone number here"
            ></b-form-input>
          </b-col>
          <b-col cols="12">
            <b-form-textarea
              v-model="wish"
              id="textarea-no-resize"
              placeholder="enter your wish here"
              rows="3"
              no-resize
            ></b-form-textarea>
          </b-col>
          <b-col cols="12 pt-3">
            <label>Will you be coming?</label>
            <b-form-group>
              <b-form-radio plain v-model="attend" value="Yes"
                >Yes, of course
              </b-form-radio>
              <b-form-radio plain v-model="attend" value="No"
                >No :(</b-form-radio
              >
            </b-form-group>
          </b-col>
          <b-col cols="12">
            <b-button variant="secondary" @click="postData()">
              <span v-if="loaderSubmit == false">Submit</span>
              <span v-else
                ><b-spinner label="Spinning"></b-spinner
              ></span> </b-button
          ></b-col>
        </b-row>
      </b-container>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      name: "",
      phone: "",
      wish: "",
      attend: "",
      loaderSubmit: false,
      // url:
      //   "https://api-wedding-rindu-pandu.herokuapp.com/api/wedding/post-data",
      url:
        "https://zu8bjg7t2f.execute-api.us-east-1.amazonaws.com/dev/api/wedding/users",
    };
  },
  methods: {
    postData() {
      if (
        this.name == "" ||
        this.phone == "" ||
        this.wish == "" ||
        this.attend == ""
      ) {
        this.gagal();
      } else {
        this.sendData();
      }
    },
    sendData() {
      this.loaderSubmit = true;
      var data = {
        name: this.name,
        phone: this.phone,
        wish: this.wish,
        attend: this.attend,
      };
      return new Promise((resolve, reject) => {
        axios
          .post(this.url, data)
          .then((res) => {
            this.loaderSubmit = false;
            this.sukses();
            setInterval(function () {
              location.reload();
            }, 2000);
          })
          .catch((e) => {
            reject(e);
            this.gagalPost();
          });
      });
    },
    sukses() {
      this.$swal({
        icon: "success",
        title: "Berhasil mengirim",
        text: "pesan kamu akan ditampilkan di halaman bawah website",
        confirmButtonColor: "#3085d6",
        confirmButtonText: ":)",
      }).then((result) => {
        location.reload();
      });
    },
    gagal() {
      this.$swal({
        icon: "error",
        title: "Gagal mengirim",
        text: "kamu harus mengisi semua fieldnya",
        confirmButtonColor: "red",
        confirmButtonText: ":(",
      }).then((result) => {});
    },
    gagalPost() {
      this.$swal({
        icon: "error",
        title: "Gagal mengirim",
        confirmButtonColor: "red",
        confirmButtonText: ":(",
      }).then((result) => {
        location.reload();
      });
    },
  },
};
</script>

<style scoped>
.content2 {
  background: linear-gradient(45deg, #7a1036, #ff7ebe, #f5d0e2);
  padding: 25px 20%;
}
.title {
  font-size: 30px;
  font-weight: bold;
  padding-bottom: 5%;
}
</style>
