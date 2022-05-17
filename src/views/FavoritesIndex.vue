<script>
import axios from "axios";
export default {
  data: function () {
    return {
      favorites: [],
    };
  },
  created: function () {
    this.indexFavorites();
  },

  methods: {
    indexFavorites: function () {
      axios.get("/favorites").then((response) => {
        console.log("favorites index", response);
        this.favorites = response.data;
      });
    },
    // createFavorite: function () {
    //   axios.post("/favorites", this.$route.params.id).then((response) => {
    //     console.log("favorites create", response);
    //     this.$router.push("/favorites");
    //   });
    // },
  },
};
</script>

<template>
  <div class="favorites-new">
    <h1>Favorites</h1>
    <div v-for="favorite in favorites" v-bind:key="favorite.id">
      <h2>{{ favorite.name }}</h2>
      <router-link :to="`/recipes/${favorite.id}`">Return to recipe</router-link>
    </div>
  </div>
</template>
