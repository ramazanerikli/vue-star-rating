<template>
  <div id="app">  
    <Rating :grade="3" :maxStars="5" :hasCounter="true" />
  </div>
</template>

<script>
import Rating from './components/Rating.vue'

export default {
  name: 'App',
  components: {
    Rating
  },
  beforeCreate: function() {
    document.body.className = 'home';
  }
}
</script>

<style lang="scss">
  @import '/styles/global.scss';
</style>