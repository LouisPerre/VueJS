<template>
  <div class="card" style="width: 18rem">
    <img :src="recipe.thumbnail_url" class="card-img-top" alt="..." />
    <div class="card-body">
      <p class="card-title">{{ recipe.name }}</p>

      <button @click="buttonClick" class="btn btn-primary">
        See the recipe
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "RecipeCard",
  props: {
    recipe: {},
  },
  methods: {
    buttonClick() {
      this.$emit("button-click");
    },
  },
};
</script>

<style scoped>
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

.card {
  height: 375px;
}

.card-body {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.card-title {
  font-size: 18px;
}
.card img {
  height: 200px;
  width: auto;
}
</style>
