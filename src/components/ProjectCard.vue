<script>
export default {
  props: {
    msg: String,
    title: String,
    description: String,
    image: String,
    categ: String,
    techs: Array,
    created: String,
  },

  methods: {
    formatData(dateString) {
      const date = new Date(dateString);
      return date.toLocaleDateString("it-IT", {
        day: "2-digit",
        month: "2-digit",
        year: "numeric",
      });
    },
  },
};
</script>

<template>
  <div class="card">
    <h1>{{ title }}</h1>
    <h3>{{ description }}</h3>
    <div class="img">
      <img :src="image" :alt="title" />
    </div>
    <p>Categoria: {{ categ }}</p>
    <p>
      Tecnologie:
      <span v-for="(tech, index) in techs" :key="tech.id">
        {{ tech.title }}<span v-if="index < techs.length - 1">,&#160;</span>
      </span>
    </p>
    <p>Creato il: {{ formatData(created) }}</p>
  </div>
</template>

<style scoped>
.card {
  background-color: rgb(146, 146, 146);
  position: relative;
  max-width: 800px;
  display: flex;
  border-radius: 15px;
  flex-direction: column;
  align-items: center;
  margin: 1rem auto;
}

.img {
  display: flex;
  justify-content: center;
  margin: 1rem 0;
  width: 300px;
  height: 500px;
}
</style>
