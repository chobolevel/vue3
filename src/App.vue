<template>
  <div class="menu">
    <a v-for="link in links" :key="link">{{ link }}</a>
  </div>
  <div v-for="(product, index) in products" :key="index">
    <h4>{{ product.name }}</h4>
    <p>{{ product.price }} 만원</p>
    <button @click="increaseReportCnt(product.id)">허위매물신고</button> <span>신고 수: {{ product.reportCnt }}</span>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      links: [ 'Home', 'Shop', 'About' ],
      products: [
        { id: 1, name: '역삼동 원룸', price: 50, reportCnt: 0 },
        { id: 2, name: '천호동 원룸', price: 60, reportCnt: 0 },
        { id: 3, name: '마로구 원룸', price: 70, reportCnt: 0 },
      ]
    }
  },
  methods: {
    increaseReportCnt(id) {
      const idx = this.products.findIndex((p) => p.id === id)
      this.products[idx].reportCnt++
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
