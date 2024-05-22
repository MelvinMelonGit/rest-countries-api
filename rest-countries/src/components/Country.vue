<script setup>
import { inject } from 'vue'

const { countries, showSingleCountryDetail } = inject('countriesKey')

</script>

<template>
  <div class="card" v-for="country in countries" :key="country.name?.official" @click="showSingleCountryDetail(country)">
    <div class="image">
      <img :src="country.flags?.svg" :alt="country.alt">
    </div>
    <div class="card-text">
      <h2>{{ country.name?.common }}</h2>
      <p>Population: {{ country.population?.toLocaleString() }}</p>
      <p>Region: {{ country.region }}</p>
      <p>Capital: {{ country.capital?.toString() }}</p>
    </div>
  </div>
</template>

<style scoped>
.card {
  box-shadow: 0px 10px 15px -3px rgba(0,0,0,0.1);
  border-radius: 0.3em;
  cursor: pointer;
}

.card:hover {
  transform: scale(1.05);
  transition: transform 0.1s;
}

.card-text {
  padding: 1em;
}

.image {
 height: 10em;
}

img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: top;
  border-top-left-radius: 0.3em;
  border-top-right-radius: 0.3em;
}
</style>