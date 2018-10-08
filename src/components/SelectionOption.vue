<template lang="pug">
  .option
    img(:src="`data:image/png;base64, ${option.image}`")
    .option__info
      checkbox(@checked="onCheck")
      .option__info__description
        .title(v-if="option.title") {{ option.title }}
        .type
          .type__text {{ option.type }}
          svg(
            xmlns='http://www.w3.org/2000/svg',
            version='1.1',
            viewBox='0 0 24 24')
            path(
              d='M13,9H11V7H13M13,17H11V11H13M12,2A10,10 0 0,0 2,12A10,10 0 0,0 12,22A10,10 0 0,0 22,12A10,10 0 0,0 12,2Z')
</template>

<script>
import Checkbox from './commons/Checkbox.vue';

export default {
  name: 'SelectionOption',
  components: { Checkbox },
  props: {
    option: {
      type: Object,
      default: () => ({}),
    },
  },
  methods: {
    onCheck(checked) {
      return `Checkbox is checked: ${checked}`;
    },
  },
};
</script>

<style scoped lang="sass">
  @import '../sass/variables.sass'

  .option
    display: flex
    flex-direction: column
    img
      width: 100%
    .option__info
      padding: 0.625rem
      background-color: lighten($color-gray, 45%)
      display: flex
      align-items: center
      .option__info__description
        font-size: 0.9rem
        .title
          &:after
            content: ':'
        .type
          display: flex
          align-items: center
          .type__text
            padding-right: 0.125rem
          svg
            width: 1rem
            height: 1rem
            margin-top: -0.375rem
            path
              fill: $color-primary
</style>
