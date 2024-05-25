<template>
  <h1>Countries of the world</h1>
  <div class="btn-container">

    <!-- <template v-for="continent in continents">
      <div v-if="(continent === $route.params.continent) || (!$route.params.continent && continent === 'ALL')">{{ continent }}</div>
      <TButton  v-else :label="continent" @clicked="onClicked(continent)"/>
    </template> -->
    <TButton
      v-for="continent in continents"
      :label="continent"
      :isDisabled="(continent === $route.params.continent) || (!$route.params.continent && continent === 'ALL')"
      @clicked="onClicked(continent)"
    />
  </div>
  <p>total count of countries is {{ countriesFiltered.length }} </p>
  <TList :items="countriesToDisplay" />
</template>

<script>

import { getCountries } from '@/data/countries.js'
import TButton from '@/components/TButton.vue'
import TList from '@/components/TList.vue'

export default {
  name: 'CountriesPage',
  computed: {
    allCountries () {
      return getCountries()
    },
    countriesFiltered () {
      return !this.$route.params.continent
        ? this.allCountries
        : this.allCountries.filter(country => country.continent.toLowerCase() === this.$route.params.continent.toLowerCase())
    },
    continents() {
      // const continents = this.countries.map(country => country.continent)
      // const continentsSet = new Set(continents)
      // return Array.from(continentsSet)
      const ar = []
      this.allCountries.forEach(country => {
        if (ar.indexOf(country.continent) < 0) {
          ar.push(country.continent)
        }
      })
      ar.unshift('ALL')
      return ar
    },
    countriesToDisplay () {
      return this.countriesFiltered.map(country => country.country)
    }
  },
  methods: {
    onClicked(continent) {
      this.$router.push(continent === 'ALL' ? '/countries' : '/countries/' + continent)
    }
  },
  components: { TButton, TList }
}

</script>

<style scoped>
.btn-container {
  display: flex;
  gap: .5rem
}
</style>