<template>
  <header-top></header-top>
  <div class="wrap-btn">
    <router-link class="btn" to="/">Back to Home</router-link>
  </div>
  <h2 class="title">{{ renderResponse.target }}</h2>
  <div class="">{{ renderResponse.value }}</div>
</template>
<script>
import HeaderTop from '@/components/HeaderTop.vue'
import allData from '@/data.json'
export default {
  components: { HeaderTop },
  created() {
      this.data = allData
  },

  data() {
    return {
      data: [],
      response: null
    }
  },
    computed: {
    renderResponse() {
      return allData.data.find(item => item.slug === this.$route.params.slug)
    }
  }
}
</script>
<style>
  .title{
    text-align: center;
    padding: 15px 0;
  }
  .wrap-btn{
    margin: 20px 0;
  }
</style>
