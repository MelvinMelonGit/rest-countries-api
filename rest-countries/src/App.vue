<script setup>
import { onMounted, provide, ref } from 'vue'
import Navbar from './components/Navbar.vue'
import CountriesDisplay from './components/CountriesDisplay.vue'

const countries = ref([])

async function getCountries() {
  const response = await fetch('https://restcountries.com/v3.1/all')
  const data = await response.json()
  countries.value = data
}

getCountries()

provide('countriesKey', countries)

</script>

<template>
  <Navbar />
  <CountriesDisplay />
</template>

<style scoped>
</style>
