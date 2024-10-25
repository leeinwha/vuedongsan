<template>
  <Transition name="fade">
    <PrdDetailModal 
      @closeModal="modal = false" 
      :Productdata="Productdata" 
      :PrdNo="PrdNo" 
      :modal="modal" 
    />
  </Transition>
  
  <div class="menu">
    <a v-for="Cate in menus" :key="Cate">{{ Cate }}</a>
  </div>
  <DiscountBanner v-if="showDiscount == true" />
  <div class="button">
    <button  @click="priceSort">가격순 정렬</button>
    <button @click="sortBack">되돌리기</button>
  </div>
  <PrdCard 
    @openModal="modal = true; PrdNo = $event" 
    :oneroom="Productdata[i]" 
    v-for="(Card,i) in Productdata" 
    :key="Card"
  />  
</template>

<script>

import PrdData from './assets/data'
import DiscountBanner from './DiscountBanner.vue';
import PrdCard from './PrdCard.vue';
import PrdDetailModal from './PrdDetailModal.vue';

export default {
  name: 'App',
  data(){
    return {
      showDiscount : true,
      PrdOriginal : [...PrdData],
      PrdNo : 0,
      Productdata : PrdData,
      modal : false,
      repCount : [0,0,0],
      menus : ['Home' , 'Shop' , 'About'],
      products : ['강남구' , '동작구' , '광진구'],
    }
  },
  methods : {
    priceSort(){
      this.Productdata.sort(function(a,b){
        return a.price - b.price
      })
    },
    sortBack(){
      this.Productdata = [...this.PrdOriginal];
    }
  },
  mounted(){
    setTimeout(()=>{
      this.showDiscount = false;
    },2000);
  },
  components: {
    DiscountBanner,
    PrdDetailModal,
    PrdCard
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
  width: 60%;
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
  margin: auto;
  width: 70%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}
.discount {
  background: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}
.fade-enter-from {
  opacity: 0;
}
.fade-enter-active {
  transition: all 0.5s;
}
.fade-enter-to {
  opacity: 1;
}
.fade-leave-from {
  opacity: 1;
}
.fade-leave-active {
  transition: all 0.5s;
}
.fade-leave-to {
  opacity: 0;
}
.button {
  margin-top: 10px;
}
.title{
  cursor: pointer;
  font-size: 20px;
  font-weight: bold;
}
@media screen and (max-width: 768px) {
  .room-img {
    width: 100%;
    margin-top: 20px;
  }
}
</style>
