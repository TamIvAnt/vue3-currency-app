<template>
  <div class="home">
    <GetCurrency msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
// @ is an alias to /src
import GetCurrency from '@/components/getCur.vue'

export default {
  name: 'Home',
  components: {
    GetCurrency
  }
}
</script>

<style lang="stylus" scoped>
  .home 
    padding-top 50px
</style>
