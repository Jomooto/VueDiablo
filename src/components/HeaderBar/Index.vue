<template>
  <header class="header-bar">
    <div class="navigation-bar">
      <b-navbar toggleable="lg"  type="dark" variant="dark">
        <b-navbar-brand v-on:to="{ name }">
          <img src="../../assets/img/diablo-iii.svg" alt="D3" width="30">
          <span class="font-diablo ml-2">D3PF</span>
        </b-navbar-brand>
      </b-navbar>
    </div>
  </header>
</template>

<script>
export default {
  data () {
    return {
      name: 'Home'
    }
  },
  name: 'HeaderBar'
}
</script>
