<template>
  <!-- Contenedor principal -->
  <div class="hero-portrait-wrapper mb-5 mb-sm-0 hover-cursor-pointer" v-on:click="goToHero(hero.id)">
    <!-- Avatar -->
    <div class="bg-secondary d-flex justify-content-center p-3 p-sm-0">
      <!-- Imagen de fondo, según la clase y el género -->
      <div v-bind:class="heroClass"></div>
    </div>
    <div class="p-2 bg-dark">
      <!-- Nombre héroe -->
      <!-- Si es hardcore, pintamos el fondo rojo -->
      <h5 class="text-truncate m-0 text-center title-name font-diablo" v-bind:class="{'bg-danger': hero.hardcore}">
        {{ hero.name }}
        <!-- Si es condicional, pintamos la hoja verde -->
        <img v-if="hero.seasonal" src="@/assets/img/leaf.png" width="12px" class="">
      </h5>
      <div class="d-flex justify-content-between border-top border-secondary pt-2 align-items-center mt-2">
        <small class="elite-kills">
          <!-- Jefes (Élites) asesinados -->
          <span class="text-monospace">{{ hero.kills.elites | formatNumber }}</span>
          Elite kills
        </small>
        <!-- Nivel. De color rojo si el héroe está muerto -->
        <small class="level-circle" v-bind:class="{'text-danger': hero.dead}"> {{ hero.level }} </small>
      </div>
    </div>
  </div>
</template>

<script>
import { formatNumber } from '@/filters/numeral'
import goToHero from '@/mixins/goToHero'

export default {
  name: 'TopHero',
  mixins: [goToHero],
  props: {
    hero: {
      type: Object,
      required: true
    }
  },
  filters: {
    formatNumber
  },
  computed: {
    heroClass () {
      const gender = this.hero.gender === 0 ? 'male' : 'female'
      var heros = `hero-${this.hero.classSlug} ${gender}`
      console.log(heros)
      return heros
    }
  }
}
</script>

<style scoped lang="stylus">
.hero-portrait-wrapper
  .title-name
    color white
    font-weight 900

  .level-circle
    width 26px
    height 26px
    padding 4px
    font-weight bold
    text-align center
    border-radius 13px
    background-color #15202b
    box-shadow 0 0 0 2px #6c757d
</style>
