<template>
  <v-app>
    <br />
    <v-container>
      <v-card elevation="9">
        <v-row>
          <v-col cols="6">
            <v-container>
              <v-img :src="data_item.link"></v-img>
              <v-row class="mt-5">
                <v-col cols="1"></v-col>
                <v-col cols="10">
                  <v-btn block color="orange"> Buy </v-btn>
                </v-col>
                <v-col cols="1"></v-col>
              </v-row>
            </v-container>
          </v-col>
          <v-col cols="6">
            {{ data_item.name }}
          </v-col>
        </v-row>
      </v-card>
    </v-container>
  </v-app>
</template>

<script>
import axios from "axios";
export default {
  layout: "newLayout",
  data() {
    return {
      data_item: [],
    };
  },
  computed: {
    id() {
      return this.$route.params.id;
    },
  },
  async mounted() {
    const res = await axios.get("http://localhost:8000/all/" + this.id);
    this.data_item = res.data;
    console.log(res.status);
    if (res.status == 200) {
    }
  },
};
</script>

<style></style>
