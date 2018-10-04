<template lang="pug">
  .glasses-advise
    .glasses-advise__header
      .glasses-advise__header__titles(:class="{'secondary-color': swap}")
        h1 BRILLENBERATER
        .glasses-advise__header__subtitle In wenigen Shritten zur perfekten Brille
      .glasses-advise__header__image
        img(src="img/header_img.png")
    .glasses-advise__breadcrumbs
      bread-crumbs
    .glasses-advise__options--container
      h2 {{ optionsTitle }}
      .glasses-advise__options
        selection-option.glasses-advise__option.glasses(
          v-if="next"
          v-for="singleGlasses in glasses"
          :key="singleGlasses.id"
          :option="singleGlasses")
        selection-option.glasses-advise__option.faces(
          v-if="!next"
          v-for="face in faces"
          :key="face.id"
          :option="face")
    .glasses-advise__options__navigation(:class="{next: !next}")
      navigation-button(
        v-if="next"
        back
        :disabled="isDisabled"
        @click="goBack") ZURICK
      navigation-button(
        v-else
        next
        @click="goNext") WEITER
    .glasses-advise__selected
      .glasses-advise__selected__title
        span Produkte, die Ihren Wunshen entshprehen
      .glasses-advise__selected__glasses
        selected(
          v-for="selected in selectedGlasses"
          :key="selected.id"
          :selected="selected")
    .change-colors(@click="toggleTitleColor") Toggle Title Colors
</template>

<script>
import BreadCrumbs from '../components/BreadCrumbs.vue';
import SelectionOption from '../components/SelectionOption.vue';
import NavigationButton from '../components/NavigationButton.vue';
import Selected from '../components/Selected.vue';
import faces from '../utils/faces';
import glasses from '../utils/glasses';
import selectedGlasses from '../utils/selectedGlasses';

export default {
  components: {
    BreadCrumbs,
    SelectionOption,
    NavigationButton,
    Selected,
  },
  data() {
    return {
      glasses,
      faces,
      selectedGlasses,
      next: false,
      back: false,
      swap: false,
    };
  },
  computed: {
    isDisabled() {
      return this.back;
    },
    optionsTitle() {
      return this.next ? 'Welche Anforderungen stellen Sie an die Fassung' : 'Welche Gesichtsform haben Sie';
    },
  },
  methods: {
    toggleTitleColor() {
      this.swap = !this.swap;
    },
    goBack() {
      this.back = !this.back;
    },
    goNext() {
      this.next = true;
    },
  },
};
</script>

<style lang="sass" scoped>
  @import '../sass/variables.sass'

  h1, h2
    font-weight: initial

  .glasses-advise
    display: flex
    flex-direction: column
    align-items: center
    max-width: 57.5rem
    margin: 0 auto
    position: relative
    .glasses-advise__header
      position: relative
      width: 100%
      min-height: 6.25rem
      .glasses-advise__header__titles
        position: absolute
        width: 100%
        background-color: rgba($color-white, 0.3)
        top: 1.875rem
        padding: 0.8rem 0
        color: $color-primary
        text-align: center
        h1
          font-size: 2rem
          margin: 0 0 0.3rem
      @media screen and (min-width: 560px)
        .glasses-advise__header__titles
          text-align: left
          h1
            font-size: 2.8rem
          .glasses-advise__header__subtitle
            font-size: 1.2rem
      .secondary-color
        color: $color-secondary
      .glasses-advise__header__image
        width: 100%
        img
          float: right
          max-width: 100%
    .glasses-advise__breadcrumbs
      padding-top: 1.25rem
      width: 100%
    .glasses-advise__options--container
      display: flex
      flex-direction: column
      justify-content: flex-end
      width: 100%
      @media screen and (min-width: 860px)
        height: 22rem
      h2
        color: $color-primary
        text-align: center
        font-size: 1.2rem
        @media screen and (min-width: 560px)
          font-size: 1.5rem
      .glasses-advise__options
        display: flex
        flex-flow: row wrap
        margin: 0 0 0 -1rem
        .glasses-advise__option
          margin: 0 0 1rem 1rem
        .faces
          flex: 1 0 34%
          min-width: 11.25rem
          @media screen and (min-width: 860px)
            flex: 1 0 20%
        margin: 0 0 0 -1rem
        .glasses
          flex: 1 0 50%
          min-width: 12.5rem
          @media screen and (min-width: 768px)
            flex: 1 0 25%
    .glasses-advise__options__navigation
      display: flex
      align-items: center
      width: 100%
      padding: 0 0 1rem
    .next
      justify-content: flex-end
    .glasses-advise__selected
      width: 100%
      .glasses-advise__selected__title
        background-color: $color-primary
        color: $color-white
        padding: 0.8rem 1rem
        text-align: center
      .glasses-advise__selected__glasses
        padding-top: 1rem
    .change-colors
      padding: 0.6rem 1rem
      border: none
      background-color: $color-primary
      color: $color-white
      position: absolute
      top: 0
      right: 0
      cursor: pointer
      outline: none
</style>

