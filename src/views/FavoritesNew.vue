<!-- <script>
import axios from "axios";
export default {
  data: function () {
    return {
      favorites: [],
    };
  },
  created: function () {},
  methods: {
    createFavorite: function () {
      axios
        .post("/favorites", this.this.$route.params.id)
        .then((response) => {
          console.log("favorites create", response);
          this.$router.push("/favorites");
        })
      });
    },
  },
};
</script>

<template>
  <div class="favorites-new">
    <h1>Favorites</h1>
    v-on:submit="createPhoto()">
      <ul>
        <li v-for="error in errors" v-bind:key="error">{{ error }}</li>
      </ul>
      Name:
      <input type="text" v-model="recipe.name" />
      <input type="submit" value="Create" />
    </form>
  </div>
</template> -->
