<template>
  <v-main>
    <v-sheet class="mx-auto" elevation="8" max-width="100%">
      <h2 class="mx-5">Tempat Makan dan Minum</h2>
      <v-slide-group
        v-model="model"
        class="pa-4"
        active-class="success"
        show-arrows
      >
        <v-slide-item v-for="n in items" :key="n">
          <v-card
            class="ma-4 rounded-md"
            elevation="7"
            height="300"
            width="200"
            @click="go(n.id)"
          >
            <v-img :src="n.link" height="120"> </v-img>
            <v-card-subtitle>
              <strong>
                {{ n.name }}
              </strong>
            </v-card-subtitle>
            <v-card-text> Rp.{{ n.harga }}.000 </v-card-text>
            <v-rating
              :value="n.ratings / 2"
              color="yellow"
              dense
              half-increments
              readonly
              size="14"
            ></v-rating>
          </v-card>
        </v-slide-item>
      </v-slide-group>
    </v-sheet>
  </v-main>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      items: [],
    };
  },
  mounted() {
    axios
      .get("http://localhost:8000/makan")
      .then((res) => {
        this.items = res.data;
        console.log(this.items);
      })
      .catch((err) => {
        console.log(err);
      });
  },
  methods: {
    go(id) {
      return this.$router.push("/detail/" + id);
    },
  },
};
</script>

<style></style>
