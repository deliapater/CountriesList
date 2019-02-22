<template lang="html">
<div v-if="country" class="info-container">
  <h1>{{country.name}}</h1>
  <p>Capital: {{country.capital}}</p>
  <img :src="country.flag" :alt="country.flag" id="flags">
  <p>Population: {{country.population}}</p>
  <p>Languages: </p>
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
}

.info-container {
  display: flex;
   align-items: left;
  justify-content: left;
  flex-direction: column;
  text-align:  justify;
  min-height: 100px;
  margin-top: 50px;
  margin-right: 180px;
  align-items: center;
}

p {
  margin: 5px;
}

li {
list-style-type: none;
 margin: 0;
 padding: 0;
}
</style>
