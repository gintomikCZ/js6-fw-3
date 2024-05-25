<template>
  <h1>Countries of the world</h1>
  <div class="btn-container">
    <TButton v-for="continent in continents" :label="continent" @clicked="onClicked(continent)"/>
  </div>
  <p>total count of countries is {{ countriesFiltered.length }} </p>
  <TList :items="countriesToDisplay" />
</template>

<script>
import { getCountries } from '@/data/countries.js'
import TButton from '@/components/TButton.vue'
import TList from '@/components/TList.vue'

export default {
  name: 'App',
  data () {
    return {
      continent: ''
    }
  },
  computed: {
    allCountries () {
      return getCountries()
    },
    countriesFiltered () {
      return !this.continent
        ? this.allCountries
        : this.allCountries.filter(country => country.continent === this.continent)
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
      this.continent = continent === 'ALL' ? '' : continent
    }
  },
  components: { TButton, TList }
}

</script>

<style scoped>
p {
  font-weight: bold
}
</style>