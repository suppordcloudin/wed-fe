<template>
  <div class="containerz">
    <div class="cardz">
      <b-row>
        <b-col cols="12">
          <b-form @submit.stop.prevent>
            <label for="text-password">Username</label>
            <b-input
              type="text"
              id="text-password"
              v-model="uname"
              @keyup.enter="login()"
              aria-describedby="password-help-block"
            ></b-input>
            <label for="text-password">Password</label>
            <b-input
              type="password"
              id="text-password"
              v-model="pass"
              @keyup.enter="login()"
              aria-describedby="password-help-block"
            ></b-input>
          </b-form>
          <b-button class="mt-3" @click="login()" variant="secondary"
            >Login</b-button
          >
        </b-col>
      </b-row>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      uname: "",
      pass: "",
      auth: "",
    };
  },
  methods: {
    login() {
      if (this.uname == "admin" && this.pass == "r1ndup4ndu") {
        console.log("logged in");
        localStorage.setItem("auth", "login");
        this.$router.push({ name: "Attendance" });
        location.reload();
        // let val = localStorage.getItem('auth');
      } else {
        this.gagal();
      }
    },
    gagal() {
      this.$swal({
        icon: "error",
        title: "Gagal login",
        text: "username atau password salah",
        confirmButtonColor: "red",
        confirmButtonText: ":(",
      }).then((result) => {});
    },
  },
  created() {
    this.auth = localStorage.getItem("auth");
    if (this.auth == "login") {
      this.$router.push({ name: "Attendance" });
    }
  },
};
</script>

<style scoped>
.containerz {
  height: auto;
  width: 100%;
  padding: 0 30%;
}
.cardz {
  border-radius: 25px;
  height: auto;
  width: 100%;
  padding: 10%;
  background-color: #d9e4f5;
  background-image: linear-gradient(315deg, #d9e4f5 0%, #f5e3e6 74%);
}
</style>
