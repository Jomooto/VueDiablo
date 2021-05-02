<template>
  <div class="hero-ico d-flex align-items-center hover-cursor-pointer" v-on:click="goToHero(hero.id)">
    <span class="hero-image border" v-bind:class="heroClassImg"/>
    <span class="hero-name ml-2 font-weight-bold" v-bind:class="{'text-danger': hero.hardcore}">
      {{ hero.name }}
    </span>
    <img v-if="hero.seasonal" src="@/assets/img/leaf.png" width="12px" class="ml-2" alt="seasonal_leaf">
  </div>
</template>

<script>
import goToHero from '@/mixins/goToHero'
export default {
  name: 'HeroIco',
  mixins: [goToHero],
  props: {
    hero: {
      required: true,
      type: Object
    }
  },
  computed: {
    heroClassImg () {
      const gender = this.hero.gender === 1 ? 'female' : 'male'
      const hardcore = this.hero.hardcore ? 'border-danger' : ''
      const ico = `hero-${this.hero.classSlug} ${gender} ${hardcore}`
      console.log(ico)
      return ico
    }
  }
}
</script>

<style scoped lang="stylus">
.hero-ico
  vertical-align middle

  .hero-image
    width 30px
    height 26px
    display inline-block
    background-size 210%

  .hero-name
    height 24px
    display inline-block
</style>
