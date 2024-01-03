<template>
  <div class="menu">
    <a v-for="link in links" :key="link">{{ link }}</a>
  </div>
  <div v-for="(product, index) in products" :key="index">
    <h4>{{ product.name }}</h4>
    <p>{{ product.price }} 만원</p>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      links: [ 'Home', 'Shop', 'About' ],
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
}

.menu {
  background-color: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: white;
  padding: 10px;
}
</style>
