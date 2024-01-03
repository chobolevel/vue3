<template>
  <div class="black-bg" v-if="isPopupOpen">
    <div class="white-bg">
      <h4>상세페이지</h4>
      <p>상세페이지 내용</p>
      <button @click="closePopup">닫기</button>
    </div>
  </div>
  <div class="menu">
    <a v-for="link in links" :key="link">{{ link }}</a>
  </div>
  <div v-for="(product, index) in products" :key="index">
    <img class="room-img" :src="require(`./assets/room${index}.jpg`)" alt="방 사진">
    <h4 @click="openPopup">{{ product.name }}</h4>
    <p>{{ product.price }} 만원</p>
    <button @click="increaseReportCnt(product.id)">허위매물신고</button> <span>신고 수: {{ product.reportCnt }}</span>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      isPopupOpen: false,
      links: [ 'Home', 'Shop', 'About' ],
      products: [
        { id: 1, name: '역삼동 원룸', price: 50, reportCnt: 0 },
        { id: 2, name: '천호동 원룸', price: 60, reportCnt: 0 },
        { id: 3, name: '마로구 원룸', price: 70, reportCnt: 0 },
      ]
    }
  },
  methods: {
    openPopup() {
      this.isPopupOpen = true
    },
    closePopup() {
      this.isPopupOpen = false
    },
    increaseReportCnt(id) {
      const idx = this.products.findIndex((p) => p.id === id)
      this.products[idx].reportCnt++
    }
  }
}
</script>

<style>
body {
  margin: 0
}

div {
  box-sizing: border-box;
}

.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}

.white-bg {
  width: 100%;
  background-color: white;
  border-radius: 8px;
  padding: 20px;
}

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

.room-img {
  width: 100%;
  margin-top: 40px;
}
</style>
