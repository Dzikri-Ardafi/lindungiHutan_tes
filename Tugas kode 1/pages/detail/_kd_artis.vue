<template>
  <v-main>
    <v-app>
      <h1>blaa</h1>
    </v-app>
  </v-main>
</template>

<script>
import axios from "axios";

export default {
  layout: "newLayout",
  data() {
    return {
      id: "",
    };
  },
  computed: {
    id() {
      return this.$route.params.id;
    },
  },

  mounted() {
    axios
      .get("http://localhost:3004/artis/" + this.id)
      .then((res) => {
        console.log(res);
      })
      .catch((err) => {
        console.log(err);
      });
  },
};
</script>

<style></style>
