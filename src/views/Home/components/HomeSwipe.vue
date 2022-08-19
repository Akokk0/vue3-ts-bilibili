<template>
  <van-swipe class="my-swipe" :autoplay="3000" indicator-color="white">
    <van-swipe-item v-for="item in swiperList" :key="item.imgSrc">
      <img :src="item.imgSrc">
    </van-swipe-item>
  </van-swipe>
</template>

<script setup lang="ts">
import axios from 'axios'
import { ref } from 'vue'

interface SwiperItem{
  link: string
  imgSrc: string
}

const swiperList = ref<SwiperItem[]>([])

async function fn() {
  const { data: res } = await axios({
    url: '/swiperList',
    method: 'GET'
  })
  swiperList.value = res.result
}
fn()

</script>

<style scoped lang="less">
.my-swipe {
  img {
    width: 100%;
  }
}
</style>
