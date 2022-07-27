<template>
  <v-carousel absolute show-arrows-on-hover cycle height="300" width="100%">
    <v-carousel-item
      v-for="(item, i) in items"
      :key="i"
      :src="item.link"
    ></v-carousel-item>
  </v-carousel>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      items: [],
    };
  },
  async mounted() {
    const res = await axios.get("http://localhost:8000/makan");
    this.items = res.data;
  },
};
</script>

<style></style>
