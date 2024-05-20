<script setup>
import { ref } from 'vue'

const countries = ref([])

async function getCountries() {
  const response = await fetch('https://restcountries.com/v3.1/all?fields=name,flags')
  const data = await response.json()
  countries.value = data
}

getCountries()

</script>

<template>
  <div v-for="country in countries" :key="country.name.official">
    <p>{{ country.name.official }}</p>
    <img :src="country.flags.png">
  </div>
</template>

<style scoped>
img {
  width: 100%;
}
</style>