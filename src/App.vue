<template>
  <div class="black-bg" v-if="isPopupOpen">
    <div class="white-bg">
      <h4>{{ popupTitle }}</h4>
      <p>{{ popupContent }}</p>
      <button @click="closePopup">닫기</button>
    </div>
  </div>
  <div class="menu">
    <a v-for="link in links" :key="link">{{ link }}</a>
  </div>
  <div v-for="(room, index) in roomList" :key="index">
    <img class="room-img" :src="room.image" alt="방 사진">
    <h4 @click="openPopup(room)">{{ room.title }}</h4>
    <p>{{ room.price.toLocaleString() }}원</p>
  </div>
</template>

<script>
import { roomList } from './assets/data'

export default {
  name: 'App',
  data() {
    return {
      isPopupOpen: false,
      popupTitie: '',
      popupContent: '',
      links: [ 'Home', 'Shop', 'About' ],
      roomList: roomList
    }
  },
  methods: {
    openPopup(room) {
      this.popupTitle = room.title
      this.popupContent = room.content
      this.isPopupOpen = true
    },
    closePopup() {
      this.poupTitle = ''
      this.popupContent = ''
      this.isPopupOpen = false
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
