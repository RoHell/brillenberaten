<template>
  <div id="app">
    <glasses-advise></glasses-advise>
  </div>
</template>

<script>
import GlassesAdvise from './views/GlassesAdvise.vue';

export default {
  components: { GlassesAdvise },
};
</script>


<style lang="sass">
  @import './sass/variables.sass'

  html, body
    margin: 0
    padding: 0
    box-sizing: border-box
    *, *:before, *:after
      box-sizing: inherit
    #app
      font-family: 'Avenir', Helvetica, Arial, sans-serif
      -webkit-font-smoothing: antialiased
      -moz-osx-font-smoothing: grayscale
      color: $color-font
      padding: 1.25rem
</style>
