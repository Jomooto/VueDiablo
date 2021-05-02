<template>
  <div class="h-attriubutes">
    <!--Título-->
    <h2 class="font-diablo">Attributes</h2>

    <hr class="bg-white">

    <div class="attributes">

      <!-- Atributos Principales-->
      <div class="core">
        <hero-attribute-list v-bind:attributes="coreAttributes"/>
      </div>

      <hr>

      <!-- Atributos Secundarios-->
      <div class="secondary">
        <hero-attribute-list v-bind:attributes="secondaryAttributes"/>
      </div>

    </div>

    <hr>

    <!-- Recursos -->
    <div class="resources">
      <hero-resources v-bind:resources="resources"/>
    </div>

  </div>
</template>
<script>
import HeroAttributeList from './HeroAttributeList'
import HeroResources from './HeroResources'

const coreAtributes = ['strength', 'dexterity', 'vitality', 'intelligence']

const secondaryAtributes = ['damage', 'toughness', 'healing']

const resources = ['life', 'primaryResource', 'secondaryResource']

export default {
  name: 'HeroAtributes',
  components: {
    HeroResources,
    HeroAttributeList
  },

  props: {
    attributes: {
      required: true,
      type: Object
    }
  },
  computed: {
    coreAttributes () {
      return coreAtributes.map(item => ({ name: item, val: this.attributes[item] }))
    },
    secondaryAttributes () {
      return secondaryAtributes.map(item => ({ name: item, val: this.attributes[item] }))
    },

    resources () {
      const data = {
        classSlug: this.attributes.classSlug,
        resources: {}
      }
      resources.forEach(item => {
        data.resources[item] = { name: item, val: this.attributes[item] }
      })
      return data
    }
  }
}
</script>

<style scoped>

</style>
