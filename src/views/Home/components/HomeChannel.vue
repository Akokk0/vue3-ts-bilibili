<template>
  <van-tabs v-model:active="active">
    <van-tab :title="item.text" v-for="item in channelList" :key="item.id"></van-tab>
  </van-tabs>
</template>

<script setup lang="ts">
import { reactive, ref, toRefs } from 'vue'
import axios from 'axios'

interface NavItem{
  id: string
  text: string
}

const active = ref(0)
const channelList = ref<NavItem[]>([])

axios({
  url: '/navList',
  method: 'GET'
}).then(res => {
  channelList.value = res.data.result
})
</script>

<style scoped>

</style>
