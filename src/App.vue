<template>
  <div id="app">
    <div
      v-if="!soloDisplay"
      class="d-flex justify-content-center flex-wrap"
      style="gap: 2%"
    >
      <RecipeCard
        v-for="(recipe, index) in recipes"
        :key="index"
        :recipe="recipe"
        style="margin-bottom: 2%"
        @button-click="soloProduct(recipe)"
      />
    </div>
    <div v-else>
      <button @click="soloDisplay = false" class="btn btn-secondary backToList">
        Back to list
      </button>
      <SingleRecipe
        :name="singleRecipe.name"
        :img="singleRecipe.thumbnail_url"
        :country="singleRecipe.country"
        :instructions="singleRecipe.instructions"
      />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import RecipeCard from "./components/RecipeCard.vue";
import SingleRecipe from "./components/SingleRecipe.vue";

export default {
  name: "HelloWorld",
  components: {
    RecipeCard,
    SingleRecipe,
  },
  data() {
    return {
      recipes: "",
      soloDisplay: false,
      singleRecipe: {},
    };
  },
  methods: {
    soloProduct: function (obj) {
      this.singleRecipe = obj;
      this.soloDisplay = true;
    },
  },
  created() {
    var options = {
      method: "GET",
      url: "https://tasty.p.rapidapi.com/recipes/list",
      params: { from: "0", size: "20", tags: "under_30_minutes" },
      headers: {
        "x-rapidapi-host": "tasty.p.rapidapi.com",
        "x-rapidapi-key": "232f6d0423msh9269e200c9d5e38p1087dajsn8f02e2a06b42",
      },
    };

    axios.request(options).then((response) => {
      this.recipes = response.data.results;
    });
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#app {
  margin-top: 25px;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.backToList {
  position: absolute;
  left: 50px;
  top: 50px;
}
</style>
