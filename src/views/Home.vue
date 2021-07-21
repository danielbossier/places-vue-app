<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <div v-for="place in places" :key="place.id">
      <h2>Name: {{ place.name }}</h2>
      <p>Address: {{ place.address }}</p>
    </div>
  </div>
</template>

<style></style>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "Welcome to Vue.js!",
      places: {},
    };
  },
  created: function () {
    this.indexPlaces();
  },
  methods: {
    indexPlaces: function () {
      axios.get("http://localhost:3000/places").then((response) => {
        this.places = response.data;
        console.log("All places:", this.places);
      });
    },
  },
};
</script>
