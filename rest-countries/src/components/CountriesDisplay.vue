<script setup>
import { provide, ref } from 'vue'
import Country from './Country.vue';
import FilterRegion from './FilterRegion.vue';
import Search from './Search.vue';

const allCountries = ref([])
const countries = ref([])

const isLoading = ref(false)
const hasError = ref('')

async function getCountries() {
  try {
    isLoading.value = true
    hasError.value = ''
    const response = await fetch('https://restcountries.com/v3.1/all?fields=name,capital,region,flags,population')

    if (!response.ok) {
      throw new Error('Failed to get countries')
    }

    const data = await response.json()

    allCountries.value = data //saved as copy
    countries.value = data
  } catch (error) {
    console.error(error)
    hasError.value = error
  } finally {
    isLoading.value = false
  }
}

getCountries()

function filterCountries(region) {
  if (region !== '') return countries.value = allCountries.value.filter(country => country.region === region)
  countries.value = allCountries.value
}

function searchCountry(search) {
  if (search !== '') return countries.value = allCountries.value.filter(country => {
    const searchLength = search.length
    const countryName = country.name?.common.toLowerCase()
    //user does not need to type the entire country name for search results to filter
    return countryName.substring(0, searchLength) === search.toLowerCase().substring(0, searchLength)
  })
  countries.value = allCountries.value
}

provide('countriesKey', {
  allCountries,
  countries,
  filterCountries,
  searchCountry
})

</script>

<template>
  <main>
    <div class="spinner" v-if="isLoading"></div>
    <p class="error-message" v-if="hasError">{{ hasError }}</p>
    <section class="search-filter" v-else-if="!isLoading">
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
  justify-items: center;
}

section.search-filter  {
  display: flex;
  justify-content: space-between;
  width: 80%;
}

section.countries {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(min(100%, 12rem), 1fr));
  gap: 4em;
  width: 80%;
  margin-top: 3em;
  margin-bottom: 5em;
}

.spinner {
   width: 56px;
   height: 56px;
   border-radius: 50%;
   border: 9px solid;
   border-color: #dbdcef;
   border-right-color: #474bff;
   animation: spinner-d3wgkg 1s infinite linear;
   margin-top: 4em;
}

@keyframes spinner-d3wgkg {
   to {
      transform: rotate(1turn);
   }
}

p.error-message {
  font-size: 2rem;
  margin-top: 4em;
}
</style>