<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <div v-for="(product, index) in products" :key="index">
    <p>{{ product.name }}</p>
    <p>{{ product.price }} 만원</p>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      products: [
        { name: '역삼동 원룸', price: 50 },
        { name: '천호동 원룸', price: 60 },
        { name: '마로구 원룸', price: 70 },
      ]
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #bbc5cf;
  margin-top: 60px;
}
</style>
