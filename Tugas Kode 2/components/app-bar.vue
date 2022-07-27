<template>
  <v-main>
    <v-app-bar
      class="app-bar"
      src="https://picsum.photos/1920/1080?random"
      height="75"
      dark
      elevation="10"
    >
      <v-row>
        <v-col cols="8"></v-col>

        <v-autocomplete
          dense
          outlined
          solo
          @click="search"
          @change="onchange"
          ref="country"
          v-model.number="id"
          item-text="name"
          item-value="id"
          :items="names"
          label="Cari Barang"
          placeholder="Select..."
          required
        ></v-autocomplete>
      </v-row>
    </v-app-bar>
  </v-main>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      id: null,
      dialog: false,
      id_: null,
      names: [],
    };
  },
  methods: {
    async search() {
      const response = await axios.get("http://localhost:8000/all");
      this.names = response.data;
      console.log("ss", this.names);
    },
    async onchange(id) {
      return this.$router.push("/detail/" + id);
    },
  },
};
</script>
<style>
.field {
  margin-top: 100px;
}
</style>
