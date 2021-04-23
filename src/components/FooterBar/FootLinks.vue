<template>
  <div>
    <b-nav small align="start">
      <b-nav-item v-on:to="{name}">Home</b-nav-item>
      <b-nav-item v-on:to="{name1}">About</b-nav-item>
      <b-nav-item href="https://github.com/baumannzone/diablo3-vue-platzi" target="_blank">Github</b-nav-item>
    </b-nav>
  </div>
</template>

<script>
export default {
  data () {
    return {
      name: 'Home',
      name1: 'About'
    }
  },
  name: 'FootLinks'
}
</script>
