<template>
  <div class="home">
    <Content1 id="wedding" />
    <Content2 />
    <Content3 />
    <Content4 />
    <Content5 />
    <Content6 />
    <Content7 id="wishes" />
    <Footer />
  </div>
</template>

<script>
// @ is an alias to /src
import Content1 from "@/components/content/Content1.vue";
import Content2 from "@/components/content/Content2.vue";
import Content3 from "@/components/content/Content3.vue";
import Content4 from "@/components/content/Content4.vue";
import Content5 from "@/components/content/Content5.vue";
import Content6 from "@/components/content/Content6.vue";
import Content7 from "@/components/content/Content7.vue";
import Footer from "@/components/Footer.vue";

export default {
  components: {
    Content1,
    Content2,
    Content3,
    Content4,
    Content5,
    Content6,
    Content7,
    Footer,
  },
};
</script>
