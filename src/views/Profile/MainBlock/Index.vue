<template>
  <div class="grid-container">

    <div class="grid-item item-left">
      <h1>Izquierda</h1>
      <top-heroes v-if="hasHeroes" v-bind:heroes="topHeroes" />

      <heroes-list v-if="hasHeroesList" v-bind:heroes="heroesList"/>

      <progress-list v-bind:acts="profileData.progression"/>
    </div>
    <div class="grid-item item-right">
      <player-stats v-bind:stats="statsData"/>
    </div>
  </div>
</template>

<script>
import TopHeroes from './TopHeroes/Index'
import HeroesList from './HeroesList/Index'
import ProgressList from './ProgressList/Index'
import PlayerStats from './PlayerStats/Index'
export default {
  name: 'MainBlock',
  components: { TopHeroes, HeroesList, ProgressList, PlayerStats },
  props: {
    profileData: {
      type: Object,
      required: true
    }
  },
  computed: {
    hasHeroes () {
      return this.profileData.heroes.length > 0
    },
    topHeroes () {
      return this.profileData.heroes.slice(0, 3)
    },
    hasHeroesList () {
      return this.profileData.heroes.length > 3
    },
    heroesList () {
      return this.profileData.heroes.slice(3, this.profileData.heroes.length)
    },
    statsData () {
      const { paragonLevel, kills, timePlayed } = this.profileData
      return { paragonLevel, kills, timePlayed }
    }
  }
}
</script>

<style scoped lang="stylus">
  .grid-container
    display grid
    grid-template-columns 1fr

 .grid-item
    &.item-left
      grid-column span 1

  &.item-right
    grid-column span 1

  @media (min-width: 992px)
    .grid-container
      display grid
      grid-template-columns repeat(6, 1fr)

      .grid-item
        &.item-left
          grid-column span 4

        &.item-right
          grid-column span 2
</style>
