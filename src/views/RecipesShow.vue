<script>
import axios from "axios";
export default {
  data: function () {
    return {
      recipe: {},
      recipeIngredients: [],
    };
  },
  created: function () {
    axios.get("http://localhost:3000/recipes/" + this.$route.params.id + ".json").then((response) => {
      console.log(response.data);
      this.recipe = response.data;
    });
  },
  methods: {},
};
</script>

<template>
  <h1>Recipe</h1>
  <!-- <p>{{ recipe.name }}</p> -->
  <!-- <p>{{ recipe.ingredients }}</p> -->
  <div v-for="recipeIngredient in recipeIngredients" v-bind:key="recipeIngredients.name">
    <p>{{ recipeIngredient.name }}</p>
  </div>

  <router-link to="/recipes">Back to all recipes</router-link>
</template>
