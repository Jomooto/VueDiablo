<template>
  <div>
    <h1>Heroes List</h1>
    <div class="heroes-list border-top border-secondary mt-5 pt-5">
      <b-table v-bind:items="heroes" v-bind:fields="fields" v-bind:dark="darkTable" hover small striped stacked="sm" >
        <template v-slot:cell(name)="data">
          <hero-ico v-bind:hero="data.item"/>
        </template>
        <template v-slot:cell(class)="data">
          <hero-class-level v-bind:hero="{classSlug: data.item.class, level: data.item.level}"/>
        </template>
        <template v-slot:cell(kills)="data">
          <span>{{ data.item.kills.elites | formatNumber }}</span>
        </template>
      </b-table>
    </div>

  </div>
</template>

<script>
import HeroIco from './HeroIco'
import HeroClassLevel from './HeroClassLevel'
import { formatNumber } from '@/filters/numeral'

export default {
  name: 'HeroesList',
  components: {
    HeroIco,
    HeroClassLevel
  },
  filters: {
    formatNumber
  },
  data () {
    return {
      darkTable: true,
      fields: [
        {
          key: 'name',
          label: 'Name'
        },
        {
          key: 'class',
          label: 'Class',
          sortable: true
        },
        {
          key: 'kills',
          label: 'Elite Kills',
          sortable: true
        }
      ]
    }
  },
  props: {
    heroes: {
      required: true,
      type: Array
    }
  }
}
</script>

<style scoped>

</style>
