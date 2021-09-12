<template>
  <div class="home">
    <!-- <Calculator name='about'/> -->
    <GetCurrency name='/' msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
// @ is an alias to /src
import GetCurrency from '@/components/getCur.vue'
// import Calculator from '@/views/About.vue'

export default {
  name: 'Home',
  components: {
    GetCurrency,
    // Calculator
  }
}
</script>

<style lang="stylus" scoped>
  .home 
    padding-top 50px
</style>
