<script>
import axios from "axios";
export default {
  data: function () {
    return {
      recipe: {},
      ingredients: {},
    };
  },
  created: function () {
    axios.get("http://localhost:3000/recipes/" + this.$route.params.id + ".json").then((response) => {
      console.log(response.data, this.recipe.ingredients);
      this.recipe = response.data;
    });
    // this.indexIngredients();
  },
  methods: {
    // indexIngredients: function () {
    //   axios.get("/ingredients").then((response) => {
    //     console.log("ingredients", response);
    //     this.ingredients = response.data;
    //   });
    // },
  },
};
</script>

<template>
  <h1>Recipe</h1>
  <p>{{ recipe.name }}</p>
  <!-- <p>{{ recipe.ingredients }}</p> -->
  <div v-for="index in recipe.ingredients.length" :key="index">
    <p>{{ recipe.ingredients[index - 1].name }}</p>
  </div>
  <!-- <div v-for="ingredient in ingredients" v-bind:key="ingredient.id">
    <p>{{ ingredients.name }}</p>
  </div> -->
  <!-- <p>{{ recipe.ingredients }}</p> -->
  <!-- <div v-for="recipeIngredient in recipeIngredients" v-bind:key="recipeIngredients.id">
    <p>{{ recipeIngredient.name }}</p> -->
  <!-- </div> -->

  <router-link to="/recipes">Back to all recipes</router-link>
</template>
