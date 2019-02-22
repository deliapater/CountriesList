<template lang="html">
  <div>
    <select v-on:change="handleSelect" v-model="selectedCountry" id="country-selected">
      <option disable value="">Select Country</option>
      <option v-for="(country,index) in countries":value="index">{{country.name}}</option>
    </select>

  </div>
</template>

<script>

import { eventBus } from '../main.js'
export default {
  name: 'countries-select',
  data(){
    return {
      selectedCountry: ''
    }
  },
  props: ['countries'],
  methods: {
    "handleSelect": function(){
      eventBus.$emit('country-selected', this.selectedCountry)
    }

  }
}
</script>

<style lang="css" scoped>


#country-selected {
  margin-left: 50px;
  margin-top: 20px;
}


</style>
