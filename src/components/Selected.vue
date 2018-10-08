<template lang="pug">
  .selected
    .selected-glasses-image
      img(:src="`data:image/png;base64, ${selected.image}`")
    .selected__details
      .selected__details__title FUNCHAL
      .selected__details__attributes
        .attribute(
          v-for="attribute in selected.attributes"
          :key="attribute.id")
          checkbox(
            small
            attribute
            :disabled="attribute.disabled")
          .attribute__label {{ attribute.label }}
      .selected__details__more
        span mehr Attribute anzeigen
        svg(
          xmlns='http://www.w3.org/2000/svg',
          version='1.1',
          viewBox='0 0 24 24')
          path(d='M7.41,8.58L12,13.17L16.59,8.58L18,10L12,16L6,10L7.41,8.58Z')
    .selected__price
      .selected__price__cost
        span Rahmen inkl. Glaser & Service
        .cost__amount
          span {{ price }}
          svg(
            xmlns='http://www.w3.org/2000/svg',
            version='1.1',
            viewBox='0 0 24 24')
            path(d='M7.07,11L7,12L7.07,13H17.35L16.5,15H7.67C8.8,17.36 11.21,19 14,19C16.23,19 18.22,17.96 19.5,16.33V19.12C18,20.3 16.07,21 14,21C10.08,21 6.75,18.5 5.5,15H2L3,13H5.05L5,12L5.05,11H2L3,9H5.5C6.75,5.5 10.08,3 14,3C16.5,3 18.8,4.04 20.43,5.71L19.57,7.75C18.29,6.08 16.27,5 14,5C11.21,5 8.8,6.64 7.67,9H19.04L18.19,11H7.07Z')

      .selected__price__basket
        basket-button

</template>

<script>
import Checkbox from './commons/Checkbox.vue';
import BasketButton from './BasketButton.vue';

export default {
  components: { Checkbox, BasketButton },
  name: 'Selected',
  props: {
    selected: {
      type: Object,
      default: () => ({}),
    },
  },
  computed: {
    price() {
      return `ab ${this.selected.price}`;
    },
  },
};
</script>

<style scoped lang="sass">
  @import '../sass/variables.sass'

  .selected
    max-width: 100%
    padding: 1rem
    display: flex
    font-size: 0.9rem
    border: 0.06rem solid $color-border
    margin-bottom: 1rem
    flex-flow: row wrap
    .selected-glasses-image
      width: 100%
      img
        width: 100%
      @media screen and (min-width: 800px)
        min-width: 30%
        width: auto
        flex: 1
    .selected__details
      display: flex
      flex-direction: column
      padding: 0 0.3rem
      flex: 1
      min-width: 13.75rem
      @media screen and (min-width: 800px)
        flex: none
      .selected__details__title
        padding-bottom: 1rem
        border-bottom: 0.06rem solid $color-border
        margin-bottom: 1rem
        font-size: 1.2rem
      .selected__details__attributes
        display: flex
        flex-direction: column
        .attribute
          display: flex
          padding: 0.25rem 0
          .attribute__label
      .selected__details__more
        padding-top: 0.3rem
        font-weight: bold
        display: flex
        align-items: center
        cursor: pointer
        svg
          flex: none
          width: 1.5rem
          height: 1.5rem
          path
            fill: $color-primary
    .selected__price
      padding: 1rem 0.3rem 0
      display: flex
      flex-direction: column
      min-width: 250px
      flex: 1
      @media screen and (min-width: 800px)
        flex: none
      .selected__price__cost
        border: 0.06rem solid $color-border
        padding: 0.625rem 1rem
        margin-bottom: 0.625rem
        border-radius: 0.25rem
        font-weight: bold
        text-align: center
        span
          white-space: nowrap
        .cost__amount
          color: $color-primary
          font-size: 1.4rem
          display: flex
          align-items: center
          justify-content: center
          padding-top: 0.625rem
          svg
            flex: none
            width: 1.25rem
            height: 1.25rem
            path
              fill: $color-primary
      .selected__price__basket
    &:last-of-type
      margin-bottom: 0
</style>
