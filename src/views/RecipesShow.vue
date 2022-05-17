<script>
import axios from "axios";
export default {
  data: function () {
    return {
      recipe: {},
      ingredients: {},
      user_id: localStorage.getItem("user_id"),
    };
  },
  created: function () {
    axios.get("http://localhost:3000/recipes/" + this.$route.params.id + ".json").then((response) => {
      this.recipe = response.data;
      console.log(this.recipe.id, this.user_id);
    });
    // this.indexIngredients();
  },
  methods: {
    createFavorite: function () {
      console.log(this.recipe);
      console.log(this.recipe.id);
      axios.post("http://localhost:3000/favorites", { recipe_id: this.recipe.id }).then((response) => {
        console.log("favorites create", response, this.recipe);
        this.$router.push("/favorites");
      });
    },
  },
};
</script>

<template>
  <h1>Recipe</h1>
  <p>{{ recipe.name }}</p>
  <h2>Ingredients</h2>
  <!-- <p>{{ recipe.ingredients }}</p> -->
  <div v-for="index in recipe.ingredients.length" :key="index">
    <p>{{ recipe.ingredients[index - 1].name }}</p>
  </div>

  <h2>Instructions</h2>
  <p>{{ recipe.instructions }}</p>
  <p>{{ recipe.recipe_ingredients }}</p>

  <div v-for="ingredient in ingredients" v-bind:key="ingredient.id">
    <p>{{ ingredients.name }}</p>
  </div>

  <!-- <p>{{ recipe.ingredients }}</p> -->
  <!-- <div v-for="recipeIngredient in recipeIngredients" v-bind:key="recipeIngredients.id">
    <p>{{ recipeIngredient.name }}</p> -->
  <!-- </div> -->
  <button v-on:click="createFavorite()">Add to Favorites</button>
  <br />
  <br />
  <router-link to="/recipes">Back to all recipes</router-link>
</template>
