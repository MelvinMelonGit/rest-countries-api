<script setup>
import { provide, ref } from 'vue'
import Country from './Country.vue';
import FilterRegion from './FilterRegion.vue';
import Search from './Search.vue';

const allCountries = ref([])
const countries = ref([])

async function getCountries() {
  const response = await fetch('https://restcountries.com/v3.1/all')
  const data = await response.json()
  allCountries.value = data //saved as copy
  countries.value = data
}

getCountries()

function filterCountries(region) {
  countries.value = allCountries.value.filter(country => country.region === region)
}

provide('countriesKey', {
  allCountries,
  countries,
  filterCountries
})

</script>

<template>
  <main>
    <section class="search-filter">
      <Search />
      <FilterRegion />
    </section>
    <section class="countries">
      <Country />
    </section>
  </main>
</template>

<style scoped>
main {
  display: grid;
  place-items: center;
}

section.search-filter  {
  display: flex;
  justify-content: space-between;
  width: 80%;
}

section.countries {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 4em;
  width: 80%;
  background-color: hsl(0, 0%, 98%);
  margin-top: 5em;
}

@media screen and (min-width: 426px) and (max-width: 1024px) {
  section.countries { 
    grid-template-columns: repeat(2, 1fr);
  }
}
</style>