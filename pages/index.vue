<template>
  <div>
    <div v-if="$nuxt.isOffline">You are offline</div>
    <div class="item" v-for="item in dataList" :key="item.id">
      <p>{{item.title}}</p>
      <img :src="item.pic" alt="">
      <div>{{item.desc}}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  data() {
    return {
      dataList: [],
    }
  },
  // async mounted() {
  //   const result = await this.$axios.get('https://api.vvhan.com/api/hotlist?type=huPu')
  //   this.dataList = result.data.data
  // },
  async asyncData({ $axios }) {
    const result = await $axios.get('https://api.vvhan.com/api/hotlist?type=huPu')
    console.log(result?.data)
    return {
      dataList: result.data.data,
    }
  }
}
</script>
<style scoped>
.item {
  border-bottom: 1px solid #000;
}
</style>
