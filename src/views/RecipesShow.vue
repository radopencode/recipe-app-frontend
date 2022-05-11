<script>
import axios from "axios";
export default {
  data: function () {
    return {
      recipe: {},
    };
  },
  created: function () {
    axios.get("/recipes/" + this.$route.params.id).then((response) => {
      console.log("recipes show", response);
      this.recipe = response.data;
    });
  },
  methods: {},
};
</script>

<template>
  <div class="recipes-show">
    <h1>{{ recipe.name }}</h1>
    <h3>{{ recipe.instructions }}</h3>
    <router-link to="/recipes">Back to all recipes</router-link>
  </div>
</template>
