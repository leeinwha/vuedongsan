<template>

  <div class="black-bg" @click="modal = false" v-if="modal == true">
    <div class="white-bg">
      <h4>Title</h4>
      <p>content</p>
      <button @click="modal = false">닫기</button>
    </div>
  </div>

  <div class="menu">
    <a v-for="Cate in menus" :key="Cate">{{ Cate }}</a>
  </div>

  <div>
    <img :src="Productdata[0].image" class="room-img">
    <h4>{{ Productdata[0].title }}</h4>
    <p>{{ Productdata[0].price }} ₩</p>
  </div>  
  <div>
    <img src="./assets/room1.jpg" alt="image2" class="room-img">
    <h4>{{ products[1] }} 원룸</h4>
    <p>70 만원</p>
    <button @click="repCount[1]++">허위매물신고</button> 
    <span> 신고수 : {{ repCount[1] }}</span>
  </div>
  <div>
    <img src="./assets/room2.jpg" alt="image3" class="room-img">
    <h4>{{ products[2] }} 원룸</h4>
    <p>70 만원</p>
    <button @click="repCount[2]++">허위매물신고</button> 
    <span> 신고수 : {{ repCount[2] }}</span>
  </div>
</template>

<script>

import PrdData from './assets/data'

export default {
  name: 'App',
  data(){
    return {
      Productdata : PrdData,
      modal : false,
      repCount : [0,0,0],
      menus : ['Home' , 'Shop' , 'About'],
      products : ['강남구' , '동작구' , '광진구'],
    }
  },
  components: {

  }
}
</script>

<style>
body {
  margin: 0;
}
div{
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.menu {
  background: darkslateblue;
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
.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}
.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}
</style>
