<script>
import HelloWorld from "./components/HelloWorld.vue";
import { store } from "../src/store";
import axios from "axios";

export default {
  name: "App",
  components: {
    HelloWorld,
  },

  data() {
    return {
      projects: null,
      currentPage: 1,
      lastPage: null,
      store,
    };
  },

  mounted() {
    axios
      .get(this.store.serverIp, {
        params: {
          page: this.currentPage,
        },
      })
      .then((response) => {
        console.log(response.data.results.data);
        this.projects = response.data.results.data;
      });
  },
};
</script>

<template>
  <HelloWorld />
</template>

<style scoped></style>
