<template lang="html">
<div v-if="country" class="info-container">
  <h1>{{country.name}}</h1>
  <p>Capital: {{country.capital}}</p>
  <p>Population: {{country.population}}</p>
  <img :src="country.flag" :alt="country.flag" id="flags">
  <p>Language: </p>
  <ul v-for="language in country.languages">
      <li>{{language.name}}</li>
    </ul>

</div>

</template>

<script>
export default {
  name: 'country-details',
  props: ['country']
}
</script>

<style lang="css" scoped>

#flags {
  width:400px;height:200px;
  display: flex;
  flex-direction: row;
  justify-content: center;
}

.info-container {

}
</style>
