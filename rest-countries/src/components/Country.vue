<script setup>
import { inject, onMounted, ref } from 'vue'

const data = ref(null)
const isLoading = ref(true)
const error = ref(null)

const countries = inject('countriesKey')

</script>

<template>
  <div class="card" v-for="country in countries" :key="country.name.official">
    <div class="image">
      <img :src="country.flags.svg" :alt="country.alt">
    </div>
    <div class="card-text">
      <h3>{{ country.name.common }}</h3>
      <p>Population: {{ country.population.toLocaleString() }}</p>
      <p>Region: {{ country.region }}</p>
      <p>Capital: {{ country.capital?.toString() }}</p>
    </div>
  </div>
</template>

<style scoped>
.card {
  box-shadow: 0px 10px 15px -3px rgba(0,0,0,0.1);
  border-radius: 0.3em;
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