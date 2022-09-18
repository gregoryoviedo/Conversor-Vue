<template>
  <header class="header-page">{{ title }} <img v-bind:src="require('./../assets/Paypal.png')" alt=""> </header>
</template>
<script>
export default {
  name: "Header",
  props: {
    title: String,
  },
};
</script>
<style scoped>
header {
  text-align: center;
  background: linear-gradient(to right, #5679de, #19337c);
  color: #eee;
  padding: 1rem;
  font-weight: bold;
  font-size: 2rem;
}

img {
  width: 50px;
  height: 50px;
}
</style>
