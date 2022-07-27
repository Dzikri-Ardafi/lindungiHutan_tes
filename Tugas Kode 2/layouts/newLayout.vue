<template>
 
    <v-app id="app">
      <app-bar/>
      <Nuxt />
    </v-app>

</template>

<script>
import appBar from '../components/app-bar.vue';
export default {
  components: { appBar },};
</script>

<style>
#app{
  background: linear-gradient(to bottom right, #d1ffd8, #ffffff);
}
</style>
