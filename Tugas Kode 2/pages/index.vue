<template>
  <v-app>
    <v-container class="carousel">
      <v-row>
        <v-col cols="8">
          <carousel />
        </v-col>

        <v-col cols="4" class="my-3">
          <a href="https://www.instagram.com/lindungihutan/">
            <v-img
              class="my-1 mx-auto rounded-xl"
              width="350"
              height="120"
              src="https://lindungihutan.com/public/campaigns/large/11604910325aerfjepm4fi0iffugrgg3lzdgu42mxyyldo21285.png"
            >
            </v-img
          ></a>

          <a href="https://www.instagram.com/lindungihutan/">
            <v-img
              class="my-1"
              src="https://www.telkomsel.com/sites/default/files/content/blogs/banner/desktop/BANNER-Recovered_3.jpg"
            >
            </v-img>
          </a>
        </v-col>
      </v-row>
    </v-container>
    <hr />
    <v-container>
      <br />
      <Slide />
      <br />

      <br />
      <Slide_pakaian />
    </v-container>
  </v-app>
</template>

<script>
import carousel from "../components/carousel.vue";
import Slide from "../components/slide_makan.vue";
import Slide_pakaian from "../components/slide_pakaian.vue";
export default {
  components: { carousel, Slide, Slide_pakaian },
  layout: "newLayout",
  data() {
    return {};
  },
};
</script>

<style></style>
