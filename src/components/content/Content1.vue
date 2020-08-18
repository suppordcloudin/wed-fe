<template>
  <div class="content1 h-100">
    <b-container class="bv-example-row text-left">
      <b-row>
        <b-col cols="6" class="text-right">
          <div data-aos="fade-right" data-aos-duration="3000">
            Rindu
          </div>
        </b-col>
        <b-col cols="12" class="text-center">&</b-col>
        <b-col cols="6"></b-col>
        <b-col cols="6" class="text-left">
          <div data-aos="fade-left" data-aos-duration="3000">
            Pandu
          </div>
        </b-col>
        <b-col cols="12" class="text-center font-normal">
          <vue-typer
            :text="option"
            :repeat="Infinity"
            :shuffle="false"
            initial-action="typing"
            :pre-type-delay="70"
            :type-delay="70"
            :pre-erase-delay="2000"
            :erase-delay="250"
            erase-style="select-all"
            :erase-on-complete="false"
            caret-animation="blink"
          ></vue-typer>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
export default {
  data() {
    return {
      option: [
        "We're getting married.",
        "Thursday the 3rd of September, 2020",
        "Tjendana Bistro Bandung",
      ],
    };
  },
};
</script>

<style scoped>
.content1 {
  padding: 0 0 20px 0;
  font-family: "Italianno";
  font-size: 80px;
}
@media only screen and (max-width: 988px) {
  .content1::before {
    content: "";
    background-image: url("../../assets/images/full2.jpg");
    background-size: cover;
    position: absolute;
    top: 0px;
    right: 0px;
    bottom: 0px;
    left: 0px;
    opacity: 0.3;
  }
}
@media only screen and (min-width: 990px) {
  .content1::before {
    content: "";
    background-image: url("../../assets/images/full.jpg");
    background-size: cover;
    position: absolute;
    top: 0px;
    right: 0px;
    bottom: 0px;
    left: 0px;
    opacity: 0.3;
  }
}

.font-normal {
  font-size: 20px;
  font-family: "Montserrat";
}
::v-deep .vue-typer .custom.char.typed {
  color: red;
  font-weight: bold;
  font-size: 15px;
}
::v-deep .vue-typer .custom.char.selected {
  font-size: 15px;
}
</style>
