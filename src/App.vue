<template>
  <div class="app">
    <MyHeader title="购物车案例" background="yellow" color="red"></MyHeader>

    <MyGoods v-for="item in gootList" :key="item.gods_id" :goods=item></MyGoods>
    <MyFooter :gootList="gootList"></MyFooter>
  </div>
</template>

<script>
import MyFooter from '@/components/MyFooter.vue'
import MyGoods from '@/components/MyGoods.vue'
import MyHeader from '@/components/MyHeader.vue'
import axios from 'axios'
export default {
  components: {
    MyFooter,
    MyGoods,
    MyHeader
  },
  data() {
    return {
      gootList: []
    }
  },
  created() {
    this.hanshu()
  },
  methods: {
    async hanshu() {
      const res = await axios({
        url: 'api/cart'
      })
      console.log(res.data.list)
      this.gootList = res.data.list
    }
  }
}
</script>

<style>
.app {
  padding: 50px 0;
}
</style>
