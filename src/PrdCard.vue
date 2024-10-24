<template>
  <div>
    <img :src="oneroom.image" class="room-img">
    <h4 @click="$emit('openModal',oneroom.id)">{{ oneroom.title }}</h4>
    <p>{{ oneroom.price }} ₩</p>
  </div>
</template>

<script>
export default {
  name:'PrdCard',
  props : {
    oneroom : Object,
  }
}
</script>

<style>

</style>

<!-- v-for="(Product,i) in Productdata" :key="i" @click="modal = true; PrdNo = i" -->