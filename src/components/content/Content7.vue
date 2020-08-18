<template>
  <div class="content2">
    <b-container class="bv-example-row text-center">
      <b-row>
        <b-col cols="12 title"
          >Wi<label style="border-bottom: 2px solid red;">sh</label>es</b-col
        >
        <b-col cols="12">
          <hooper
            :infinite-scroll="true"
            :center-mode="true"
            :auto-play="true"
            :play-speed="2000"
            :wheel-control="false"
            :touch-drag="false"
            :keys-control="false"
          >
            <slide v-for="(item, index) in images" :key="'item' + index">
              <b-row>
                <b-col>
                  <div class="pt-5">
                    "{{ item.wish }}" - <small>{{ item.name }}</small>
                  </div>
                </b-col>
              </b-row>
            </slide>

            <hooper-navigation slot="hooper-addons"></hooper-navigation>
          </hooper>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import { Hooper, Slide, Navigation as HooperNavigation } from "hooper";
import "hooper/dist/hooper.css";
import axios from "axios";
export default {
  components: {
    Hooper,
    Slide,
    HooperNavigation,
  },
  data() {
    return {
      slide: 0,
      sliding: null,
      images: [],
      url: "https://api-wedding-rindu-pandu.herokuapp.com/api/wedding/get-data",
    };
  },
  created() {
    this.getData();
  },
  methods: {
    getData() {
      return new Promise((resolve, reject) => {
        axios
          .get(this.url)
          .then((response) => {
            this.images = response.data;
          })
          .catch((e) => {
            reject(e);
          });
      });
    },
  },
};
</script>

<style scoped>
.content2 {
  padding: 50px;
}
.title {
  font-size: 50px;
  font-weight: bold;
  padding-bottom: 5%;
}
</style>
