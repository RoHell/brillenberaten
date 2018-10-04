<template lang="pug">
  .basket-button(@click="$emit('click')")
    svg(
      xmlns='http://www.w3.org/2000/svg',
      xmlns:xlink='http://www.w3.org/1999/xlink',
      version='1.1',
      viewBox='0 0 24 24')
      path(d='M17,18A2,2 0 0,1 19,20A2,2 0 0,1 17,22C15.89,22 15,21.1 15,20C15,18.89 15.89,18 17,18M1,2H4.27L5.21,4H20A1,1 0 0,1 21,5C21,5.17 20.95,5.34 20.88,5.5L17.3,11.97C16.96,12.58 16.3,13 15.55,13H8.1L7.2,14.63L7.17,14.75A0.25,0.25 0 0,0 7.42,15H19V17H7C5.89,17 5,16.1 5,15C5,14.65 5.09,14.32 5.24,14.04L6.6,11.59L3,4H1V2M7,18A2,2 0 0,1 9,20A2,2 0 0,1 7,22C5.89,22 5,21.1 5,20C5,18.89 5.89,18 7,18M16,11L18.78,6H6.14L8.5,11H16Z')
    .basket-button__title Zum Produkt
    .basket-button__arrow
      svg(
        xmlns='http://www.w3.org/2000/svg',xmlns:xlink='http://www.w3.org/1999/xlink',
        version='1.1',
        viewBox='0 0 24 24')
        path(d='M4,15V9H12V4.16L19.84,12L12,19.84V15H4Z')
</template>

<script>
export default {
  name: 'BasketButton',
};
</script>

<style scoped lang="sass">
  @import '../sass/variables.sass'

  .basket-button
    padding: 0.625rem
    background: linear-gradient(lighten($color-secondary, 7%), $color-secondary)
    border-radius: 0.375rem
    display: flex
    justify-content: space-between
    align-items: center
    cursor: pointer
    svg
      width: 1.5rem
      height: 1.5rem
      path
        fill: $color-white
    .basket-button__title
      font-weight: 800
      font-size: 1.2rem
      padding: 0 1rem
      color: $color-white
      text-shadow: 0.06rem 0.06rem 0 darken($color-gray, 30%)
    .basket-button__arrow
      width: 1.75rem
      height: 1.75rem
      border-radius: 50%
      box-shadow: inset 0 0 0.625rem darken($color-secondary, 20%)
      background-color: lighten($color-secondary, 10%)
      display: flex
      align-items: center
      justify-content: center
      svg
        width: 1.3rem
        height: 1.3rem
        path
          fill: $color-white
</style>
