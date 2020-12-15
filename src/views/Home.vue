<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <div v-for="place in places">{{ place.name }}</div>
  </div>
</template>

<style>
</style>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "Places",
      places: [],
    };
  },
  created: function () {
    this.placesIndex();
  },
  methods: {
    placesIndex: function () {
      axios.get("/api/places").then((response) => {
        console.log(response.data);
        this.places = response.data;
      });
    },
  },
};
</script>
