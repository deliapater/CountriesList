<template lang="html">
  <div>
    <h1>Countries</h1>
    <div class="main-container">
      <input id="search-bar" type="text" v-model="search" placeholder="search for country..." v-on:keyup="searchForCountry">
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
  },

methods: {
    searchForCountry: function(){
      let foundCountry = this.countries.find((country) => {
        // return country.name.toLowerCase() === this.search.toLowerCase()
        return country.name.toLowerCase().indexOf(this.search.toLowerCase()) > -1
      })
      this.selectedCountry = foundCountry
    }
  }
}
</script>

<style lang="css" scoped>

  #search-bar {
    display: flex;
    justify-content: center;
    width:300px;height:20px;
    margin-left: 50px;

  }

  h1 {
    display: flex;
    justify-content: center;
    margin: 20px;
    background-color: black;
    color: white
  }
</style>
