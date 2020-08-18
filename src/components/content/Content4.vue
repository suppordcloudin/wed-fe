<template>
  <div class="content2">
    <b-container class="bv-example-row text-left">
      <b-row>
        <b-col cols="12 mb-5" md="4">
          <div
            data-aos="zoom-in-down"
            data-aos-delay="100"
            data-aos-duration="500"
          >
            <b-row>
              <b-col cols="3">
                <b-icon class="op" icon="map" font-scale="3"></b-icon>
              </b-col>
              <b-col cols="9">
                <b-row>
                  <b-col cols="12 bold">Venue</b-col>
                  <b-col cols="12">Tjendana Bistro Bandung</b-col>
                </b-row>
              </b-col>
            </b-row>
          </div>
        </b-col>
        <b-col cols="12 mb-5" md="4">
          <div
            data-aos="zoom-in-down"
            data-aos-delay="300"
            data-aos-duration="500"
          >
            <b-row>
              <b-col cols="3">
                <b-icon
                  class="op"
                  icon="calendar2-check"
                  font-scale="3"
                ></b-icon>
              </b-col>
              <b-col cols="9">
                <b-row>
                  <b-col cols="12 bold">Date</b-col>
                  <b-col cols="12">Thursday the 3rd of September, 2020</b-col>
                </b-row>
              </b-col>
            </b-row>
          </div>
        </b-col>
        <b-col cols="12 mb-5" md="4">
          <div
            data-aos="zoom-in-down"
            data-aos-delay="500"
            data-aos-duration="500"
          >
            <b-row>
              <b-col cols="3">
                <b-icon class="op" icon="clock" font-scale="3"></b-icon>
              </b-col>
              <b-col cols="9">
                <b-row>
                  <b-col cols="12 bold">Time</b-col>
                  <b-col cols="12">16:00 - 19:00 WIB</b-col>
                </b-row>
              </b-col>
            </b-row>
          </div>
        </b-col>
        <b-col cols="12 text-center">
          <b-row>
            <b-col cols="12 bold">
              {{ day }}d : {{ hour }}h : {{ minute }}m : {{ second }}s
            </b-col>
            <b-col cols="12">to go <b-icon icon="star"></b-icon></b-col>
          </b-row>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
export default {
  data() {
    return {
      day: 0,
      hour: 0,
      minute: 0,
      second: 0,
    };
  },
  mounted() {
    var self = this;
    setInterval(function () {
      self.setTime();
    }, 1000);
  },
  methods: {
    setTime() {
      var countDownDate = new Date("Aug 9, 2020 15:37:25").getTime();

      var now = new Date().getTime();
      var distance = countDownDate - now;
      this.day = Math.floor(distance / (1000 * 60 * 60 * 24));
      this.hour = Math.floor(
        (distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60)
      );
      this.minute = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
      this.second = Math.floor((distance % (1000 * 60)) / 1000);
      if (distance < 0) {
        clearInterval(x);
        document.getElementById("demo").innerHTML = "EXPIRED";
      }
    },
  },
};
</script>

<style scoped>
.content2 {
  padding-bottom: 25px;
}
.name {
  font-weight: bold;
  font-size: 25px;
}
.op {
  opacity: 0.5;
}
.bold {
  font-weight: bold;
}
</style>
