<template>
  <div id="app">
    <LoadLayout v-if="isLoading">
      <BaseLoading/>
    </LoadLayout>
    <MainLayout v-else />
  </div>

</template>

<style lang="stylus">
#app
  padding 60px 0
  font-family 'Avenir', Helvetica, Arial, sans-serif
  -webkit-font-smoothing antialiased
  -moz-osx-font-smoothing grayscale
  color #ffffff // Le ponemos un color de letra blanco para que resalte
  background-color #15202b // Le cambiamos el color de fondo por un azul marino oscuro

</style>
<script>
import { mapState } from 'vuex'
import LoadLayout from './layouts/LoadLayout'
import MainLayout from './layouts/MainLayout'
import BaseLoading from './components/BaseLoading'
export default {
  components: { LoadLayout, MainLayout, BaseLoading },
  computed: {
    ...mapState('loading', {
      isLoading: 'isLoading'
    })
  }
}
</script>
