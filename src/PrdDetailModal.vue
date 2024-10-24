<template>
  <div class="black-bg" v-if="modal == true">
    <div class="white-bg">
      <img :src="Productdata[PrdNo].image" style="width: 100%;">
      <h4>{{ Productdata[PrdNo].title }}</h4>
      <p>{{ Productdata[PrdNo].content }}</p>
      <input v-model="month">
      <p>{{ month }}개월 : {{ Productdata[PrdNo].price * month }} ₩</p>
      <button @click="$emit('closeModal')">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'PrdDetaileModal',
  data() {
    return {
      month : 1,
    }
  },
  watch : {
    month(a) {
      if(a >= 13){
        alert('13보다 작은 수를 입력해주세요')
      }
    },
  },
  props : {
    Productdata : Array,
    PrdNo : Number,
    modal : Boolean,
  }
}
</script>

<style>

</style>