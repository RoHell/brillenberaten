<template lang="pug">
  label.checkbox-container(:class="checkboxClass")
    input(
      type="checkbox"
      v-model="checked"
      @change="checkChange")
    .checkbox
      .checkmark(v-if="isCheckmarkVisible")
</template>

<script>
export default {
  name: 'Checkbox',
  props: {
    small: {
      type: Boolean,
      default: false,
    },
    disabled: {
      type: Boolean,
      default: false,
    },
    attribute: {
      type: Boolean,
      default: false,
    },
  },
  data() {
    return {
      checked: false,
    };
  },
  computed: {
    checkboxClass() {
      return [
        { 'checkbox--small': this.small },
        { 'checkbox--disabled': this.disabled },
        { 'checkbox--attribute': this.attribute },
      ];
    },
    isCheckmarkVisible() {
      return this.checked || this.disabled || this.attribute;
    },
  },
  methods: {
    checkChange() {
      this.$emit('checked', this.checked);
    },
  },
};
</script>

<style scoped lang="sass">
  @import '../../sass/variables.sass'
  .checkbox-container
    display: block
    position: relative
    padding-left: 1.563rem
    margin-bottom: 1rem
    cursor: pointer
    font-size: 1.375rem
    -webkit-user-select: none
    -moz-user-select: none
    -ms-user-select: none
    user-select: none
    input
      position: absolute
      opacity: 0
      cursor: pointer
      height: 0
      width: 0
    .checkbox
      content: ""
      position: absolute
      top: 0
      left: 0
      height: 1rem
      width: 1rem
      background-color: $color-white
      border: 0.06rem solid $color-border
      border-radius: 0.24rem
      .checkmark
        content: ""
        position: absolute
        left: 0.28rem
        top: 0.063rem
        width: 0.35rem
        height: 0.625rem
        border: solid $color-primary
        border-width: 0 0.2rem 0.2rem 0
        -webkit-transform: rotate(45deg)
        -ms-transform: rotate(45deg)
        transform: rotate(45deg)
  .checkbox--small
    margin-bottom: 0.75rem
    padding-left: 1.25rem
    .checkbox
      top: 0.125rem
      height: 0.75rem
      width: 0.75rem
      border: none
      background-color: lighten($color-secondary, 10%)
      border-radius: 0
      .checkmark
        width: 0.28rem
        left: 0.26rem
        height: 0.48rem
        border: solid $color-white
        border-width: 0 0.125rem 0.125rem 0
  .checkbox--disabled
    cursor: default
    pointer-events: none
    .checkbox
      background-color: $color-border
      .checkmark
        left: 0.185rem
        top: 0.189rem
        width: 0.375rem
        height: 0.375rem
        border-radius: 50%
        background-color: $color-white
        border: none
  .checkbox--attribute
    cursor: default
    pointer-events: none
</style>
