<template lang="html">
  <div>
    <h1>Countries</h1>
    <div class="main-container">
      <countries-select :countries = "countries"></countries-select>
      <country-details :country = "selectedCountry"></country-details>
    </div>
  </div>
</template>

<script>

import CountriesSelect from './components/CountriesSelect.vue';
import CountryDetails from './components/CountryDetails.vue';
import {eventBus} from './main.js';

export default {
  data(){
    return {
      countries: [],
      selectedCountry: null
    };
  },

  mounted(){
    fetch('https://restcountries.eu/rest/v2/all')
    .then(res => res.json())
    .then(countries => this.countries = countries)
    eventBus.$on("country-selected", (index) => {
      this.selectedCountry = this.countries[index];
  })
},
  components: {
    "countries-select": CountriesSelect,
    "country-details": CountryDetails
  }
}
</script>

<style lang="css" scoped>
  .main-container {
    display: flex;
    justify-content: space-between;
  }
</style>




<!--
<template lang="html">
  <div>
    <h1>Countries</h1>
    <country-select :countries="countries"></country-select>
    <country-detail :country="selectedCountry"></country-detail>
  </div>
</template>

<script>
import { eventBus } from './main.js'
import CountrySelect from './components/CountrySelect.vue'
import CountryDetail from './components/CountryDetail.vue'
export default {
  data(){
    return {
      countries: [],
      selectedCountry: null
    }
  },
  components: {
    countrySelect: CountrySelect,
    countryDetail: CountryDetail
  },
  mounted(){
    fetch('https://restcountries.eu/rest/v2/all')
    .then(res => res.json())
    .then(countries => this.countries = countries)
    eventBus.$on('country-selected', (index) => {
      this.selectedCountry = this.countries[index]
    })
  },
}
</script>

<style lang="css" scoped>
</style> -->
