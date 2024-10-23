<template>
  <div class="black-bg" v-if="modal == true">
    <div class="white-bg">
      <img :src="Productdata[PrdNo].image" style="width: 100%;">
      <h4>{{ Productdata[PrdNo].title }}</h4>
      <p>{{ Productdata[PrdNo].content }}</p>
      <p>{{ Productdata[PrdNo].price }} ₩</p>
      <!-- <button @click="modal = false">닫기</button> -->
    </div>
  </div>
</template>

<script>
export default {
  name: 'PrdDetaileModal',
  props : {
    Productdata : Array,
    PrdNo : Number,
    modal : Boolean,
  }
}
</script>

<style>

</style>