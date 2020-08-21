<template>
  <div>
    <b-navbar toggleable="lg" type="light">
      <b-container v-if="route=='Home'">
        <b-navbar-brand href="#"></b-navbar-brand>
        <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>
        <b-collapse id="nav-collapse" is-nav>
          <!-- Right aligned nav items -->
          <b-navbar-nav class="ml-auto">
            <!-- Using 'button-content' slot -->
            <b-nav-item href="#wedding">Wedding</b-nav-item>
            <b-nav-item href="#video">Video</b-nav-item>
            <b-nav-item href="#attendance">Attendance</b-nav-item>
            <b-nav-item href="#wishes">Wishes</b-nav-item>
          </b-navbar-nav>
        </b-collapse>
      </b-container>
      <b-container v-else>
        <b-navbar-brand href="#"></b-navbar-brand>
        <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>
        <b-collapse id="nav-collapse" is-nav>
          <!-- Right aligned nav items -->
          <b-navbar-nav class="ml-auto">
            <!-- Using 'button-content' slot -->
            <b-nav-item href="/">Home</b-nav-item>
          </b-navbar-nav>
        </b-collapse>
      </b-container>
    </b-navbar>
  </div>
</template>
<script>
export default {
  data() {
    return {
      route: ''
    };
  },
  methods: {
  },
  mounted(){
    this.route = this.$route.name
  }
};
</script>

<style scoped>
.navbar-light .navbar-nav .nav-link {
  color: black;
  color: black;
  font-weight: bold;
}
.navbar-nav > li {
  padding-left: 30px;
}
.navbar {
  z-index: 5;
}
</style>
