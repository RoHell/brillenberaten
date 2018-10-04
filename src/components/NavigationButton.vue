<template lang="pug">
  .nav-button(@click="$emit('click')" :class="{disabled: disabled}")
    .nav-button__title(v-if="next")
      slot
    .nav-button__direction
      .nav-button__direction__mark(:class="{back: back, next: next}")
    .nav-button__title(v-if="back")
      slot
</template>

<script>
export default {
  name: 'NavigationButton',
  props: {
    next: {
      type: Boolean,
      default: false,
    },
    back: {
      type: Boolean,
      default: false,
    },
    disabled: {
      type: Boolean,
      default: false,
    },
  },
};
</script>

<style scoped lang="sass">
  @import '../sass/variables.sass'
  .nav-button
    display: flex
    align-items: center
    justify-content: space-between
    cursor: pointer
    .nav-button__direction
      width: 2.5rem
      height: 2.5rem
      background-color: $color-primary
      position: relative
      .nav-button__direction__mark
        position: absolute
        content: ''
        top: 0.625rem
        width: 1.125rem
        height: 1.125rem
        border: solid $color-white
        border-width: 0.06rem 0.06rem 0 0
      .back
        right: 0.3rem
        -webkit-transform: rotate(225deg)
        -ms-transform: rotate(225deg)
        transform: rotate(225deg)
      .next
        left: 0.3rem
        -webkit-transform: rotate(45deg)
        -ms-transform: rotate(45deg)
        transform: rotate(45deg)
    .nav-button__title
      padding: 0 1rem
      font-weight: 600
      color: $color-primary
  .disabled
    cursor: default
    pointer-events: none
    .nav-button__direction
      background-color: $color-border
    .nav-button__title
      color: $color-font
</style>
