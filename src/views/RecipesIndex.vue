<script>
import axios from "axios";
export default {
  data: function () {
    return {
      recipes: [],
    };
  },
  created: function () {
    this.indexRecipes();
  },
  methods: {
    indexRecipes: function () {
      axios.get("/recipes").then((response) => {
        console.log("recipes index", response);
        this.recipes = response.data;
      });
    },
  },
};
</script>

<template>
  <h1>HERE ARE recipes</h1>
  <div class="recipes-index">
    <h1>All Recipes</h1>
    <div v-for="recipe in recipes" v-bind:key="recipe.id">
      <h2>{{ recipe.name }}</h2>
      <router-link v-bind:to="`/recipes/${recipe.id}`">More details</router-link>
    </div>
  </div>
</template>
``
