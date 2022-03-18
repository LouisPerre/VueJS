<template>
  <div id="singleRecipe">
    <h3>{{ name }}</h3>
    <img :src="img" alt="..." />
    <div>
      <h5 class="my-4">Country: {{ country }}</h5>
      <div v-for="instruction in instructions" :key="instruction">
        <p>{{ instruction.display_text }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SingleRecipe",
  props: {
    name: String,
    img: String,
    country: String,
    instructions: [],
  },
};
</script>

<style scoped>
img {
  width: 500px;
  margin: 20px 0px;
}
#singleRecipe {
  margin-top: 100px;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 0px 15%;
}
</style>
