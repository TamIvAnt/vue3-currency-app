<template>
  <div id="nav">
    <Headers></Headers>
    
  </div>
  <router-view/>
</template>

<script>
import Headers from '@/components/headers.vue'

export default {
  name: 'Home',
  components: {
    Headers
  },
  
}
</script>

<style lang="stylus">
@import url('https://fonts.googleapis.com/css2?family=Lato:ital,wght@0,400;0,700;0,900;1,400&display=swap')

.text
  color #EEEEEE
  max-width 215px
  width 100%

body
  margin 0
  background #222831
  font-family 'Lato', sans-serif
#app
  font-family 'Lato', sans-serif
  -webkit-font-smoothing antialiased
  -moz-osx-font-smoothing grayscale
  text-align center
  color #2c3e50
  // margin-top 60px
a
  text-decoration: none
  color #00ADB5

.container
  max-width 1110px
  margin 0 auto



</style>
