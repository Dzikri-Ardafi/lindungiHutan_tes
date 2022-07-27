<template>
  <v-container>
    <h1>assalamualaikum</h1>

    <v-row>
      <v-col v-for="arts in peoples" :key="arts.id">
        <v-card class="mx-auto" max-width="344">
          <v-img :src="arts.img_path" max-height="200px"> </v-img>

          <v-card-title> {{ arts.nm_artis }} </v-card-title>

          <v-card-subtitle>
            Country : {{ arts.negara }}
            <span
              ><v-avatar size="25"> <img :src="arts.negara_path" /> </v-avatar
            ></span>
          </v-card-subtitle>

          <v-card-actions>
            <v-btn color="orange lighten-2" text @click="() => goTo(arts.id)">
              Biografi
            </v-btn>

            <v-spacer></v-spacer>

            <v-btn icon @click="() => goTo(arts.id)">
              <v-icon> mdi-chevron-right </v-icon>
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
      <!-- dialog -->
      <v-dialog class="dialog" v-model="dialog" width="600px">
        <v-card color="blue lighten-5" elevation="7">
          <v-card-title>
            <v-app-bar
              style="
                background: linear-gradient(to bottom right, #0008ff, #cccccc);
              "
              id="app"
              class="rounded-xl"
            >
              <v-toolbar-title> {{ nama.nm_artis }} </v-toolbar-title>
            </v-app-bar>
          </v-card-title>
          <v-card-text>
            Lorem ipsum dolor sit amet, semper quis, sapien id natoque elit.
            Nostra urna at, magna at neque sed sed ante imperdiet, dolor mauris
            cursus velit, velit non, sem nec. Volutpat sem ridiculus placerat
            leo, augue in, duis erat proin condimentum in a eget, sed fermentum
            sed vestibulum varius ac, vestibulum volutpat orci ut elit eget
            tortor. Ultrices nascetur nulla gravida ante arcu. Pharetra rhoncus
            morbi.
          </v-card-text>
          <v-card-subtitle>
            <ol>
              Film yang pernah dimainkan :
            </ol>
            <li v-for="movie in film" :key="movie.kd_movie">
              {{ movie.nm_film }}
            </li>
          </v-card-subtitle>
          <br />

          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn color="green darken-1" text @click="dialog = false">
              Disagree
            </v-btn>
            <v-btn color="green darken-1" text @click="dialog = false">
              Agree
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </v-row>
  </v-container>
</template>

<script>
import axios from "axios";

export default {
  name: "hehePages",
  layout: "newLayout",
  data() {
    return {
      dialog: false,
      nama: [],
      film: [],
      peoples: [],
      post: {
        name: "",
        Gaji: "",
        unicId: "",
      },
    };
  },
  async mounted() {
    const response = await axios.get("http://localhost:3004/artis");
    this.peoples = await response.data;
    this.film = await response.data.others;
  },
  methods: {
    async goTo(id) {
      const res = await axios.get("http://localhost:3004/artis/" + id);
      this.film = res.data.artis;
      this.nama = res.data;
      console.log(this.nm_film);
      this.dialog = await true;
    },

    async upload() {
      const response = await axios.post(
        "http://localhost:3004/artis",
        this.post
      );
      console.log(response.data);
    },
    // async get() {
    //   const response = await axios.get("http://localhost:3004/artis/1");
    //   this.people = response.data;
    //   console.log("this", this.people);
    // },
  },
};
</script>

<style>
#app {
  background: linear-gradient(180deg, #ffffff 14.37%, #e3f5fd 100%);
}
</style>
