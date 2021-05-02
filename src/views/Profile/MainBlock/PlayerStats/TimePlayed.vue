<template>
  <div class="time-played mt-3">
    <hr class="bg-white mt-5">
    <h2 class="font-diablo my-4">Time Played</h2>
    <div class="bg-dark p-3">
      <div v-for="hero in timePlayed" v-bind:key="hero.classSlug">
        <TimePlayedHero v-bind:hero-time="hero"/>
      </div>
    </div>
  </div>
</template>

<script>
import TimePlayedHero from './TimePlayedHero'
export default {
  name: 'TimePlayed',
  components: { TimePlayedHero },
  props: {
    timePlayed: {
      required: true,
      type: Array
    }
  }

}
</script>

<style scoped>

</style>
