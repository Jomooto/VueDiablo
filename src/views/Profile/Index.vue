<template>
  <div>
    <base-loading v-if="isLoading" />
    <template v-if="profileData !== null">
      <main-block v-if="profileData !== null" v-bind:profile-data= "profileData" />
      <artisans-block v-bind:artisans-data="artisansData"/>
    </template>
  </div>
</template>

<script>
import { getApiAccount } from '@/api/search'
import setError from '@/mixins/setError'
import BaseLoading from '@/components/BaseLoading'
import MainBlock from './MainBlock/Index'
import ArtisansBlock from './ArtisanBlock/Index'
export default {
  name: 'ProfileView',
  mixins: [setError],
  data () {
    return {
      profileData: null,
      isLoading: false
    }
  },

  components: {
    BaseLoading,
    MainBlock,
    ArtisansBlock
  },
  created () {
    this.fetchData()
    this.isLoading = true
  },
  methods: {
    fetchData () {
      const { region, battleTag: account } = this.$route.params
      getApiAccount({ region, account })
        .then(({ data }) => {
          this.profileData = data
        })
        .catch((err) => {
          this.profileData = null

          const errObj = {
            routeParams: this.$route.params,
            message: err.message
          }
          this.setApiErr(errObj)
          this.$route.push({ name: 'Error' })
        })
        .finally(() => {
          this.isLoading = false
        })
    }
  },
  computed: {
    artisansData () {
      return {
        blacksmith: this.profileData.blacksmith,
        blacksmithHardcore: this.profileData.blacksmithHardcore,
        jeweler: this.profileData.jeweler,
        jewelerHardcore: this.profileData.jewelerHardcore,
        mystic: this.profileData.mystic,
        mysticHardcore: this.profileData.mysticHardcore
      }
    }
  }
}
</script>

<style scoped>

</style>
