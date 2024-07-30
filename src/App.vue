<script>
import ProjectCard from "./components/ProjectCard.vue";
import { store } from "../src/store";
import axios from "axios";

export default {
  name: "App",
  components: {
    ProjectCard,
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
      })
      .catch((error) => {
        console.log(error);
      });
  },
};
</script>

<template>
  <div v-if="projects !== undefined">
    <ProjectCard
      v-for="data in projects"
      :title="data.title"
      :description="data.description"
      :image="data.image"
      :categ="data.type.title"
      :techs="data.technologies"
      :created="data.created_at"
    />
  </div>
  <div v-else>
    <h1>No Posts Found</h1>
  </div>
</template>

<style scoped>
h1 {
  text-align: center;
}
</style>
