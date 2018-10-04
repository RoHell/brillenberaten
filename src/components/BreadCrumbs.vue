<template lang="pug">
  .breadcrumbs
    .breadcrumb(
      v-for="crumb in 5"
      :key="crumb"
      :class="{'breadcrumb--disabled': isDisabled(crumb)}"
      @click="goTo(crumb)"
    ) {{ crumb }}
</template>

<script>
export default {
  name: 'BreadCrumbs',
  methods: {
    isDisabled(crumb) {
      return [1, 2, 3, 4].includes(crumb);
    },
    goTo(crumb) {
      return `Bredcrumb nr: ${crumb} has been clicked`;
    },
  },
};
</script>

<style scoped lang="sass">
  @import '../sass/variables.sass'

  .breadcrumbs
    width: 100%
    display: flex
    .breadcrumb
      color: $color-white
      display: block
      background: $color-primary
      text-decoration: none
      position: relative
      height: 2.5rem
      line-height: 2.5rem
      padding: 0 0.625rem 0 0.3rem
      text-align: center
      margin-right: 1.5rem
      cursor: pointer
      flex: 1
      &:first-child
        &:before
          border: none
      &:last-child
        margin-right: 0
        &:after
          border: none
      &:before,
      &:after
        content: ""
        position: absolute
        top: 0
        border: 0 solid $color-primary
        border-width: 1.25rem 0.625rem
        width: 0
        height: 0
      &:before
        left: -1.25rem
        border-left-color: transparent
      &:after
        left: 100%
        border-color: transparent
        border-left-color: $color-primary
    .breadcrumb--disabled
      pointer-events: none
      cursor: default
      opacity: 0.3
</style>
