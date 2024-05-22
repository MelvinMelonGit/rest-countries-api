<script setup>
import { inject } from 'vue'

const props = defineProps({
  countryName: Object
})

const { showCountries } = inject('countriesKey')
</script>

<template>
  <section>
    <button @click="showCountries">Back</button>
    <div class="country-details">
      <div class="img-detail">
        <img :src="countryName.flags?.svg" :alt="countryName.alt">
      </div>
      <div class="full-details">
        <h2>{{ countryName.name?.common }}</h2>
        <div class="details">
          <div>
            <p>Native Name: {{ countryName.name?.nativeName?.eng?.official }}</p>
            <p>Population: {{ countryName.population?.toLocaleString() }}</p>
            <p>Region: {{ countryName.region }}</p>
            <p>Capital: {{ countryName.capital?.toString() }}</p>
          </div>
          <div>
            <p>Top Level Domain: {{ countryName.tld?.toString() }}</p>
            <p>Currencies: {{ countryName.currencies }}</p>
            <p>Languages: {{ countryName.languages }}</p>
          </div>
        </div>
        <div>
          <p>Border Countries: {{ countryName.borders?.toString()}}</p>
        </div>
      </div>
    </div>
  </section>
  
</template>

<style scoped>
button {
  padding: 1em 2em;
  background-color: white;
  box-shadow: 0px 10px 15px -3px rgba(0,0,0,0.1);
  border: 0;
  border-radius: 0.3em;
  margin-top: 4em;
  cursor: pointer;
}

button:hover {
  transform: scale(1.1);
  transition: transform 0.1s;
}

.country-details {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  margin-top: 4em;
  gap: 4em;
}

.details {
  display: flex;
  width: 50vw;
  gap: 4em;
}

img {
  width: 100%;
  object-fit: cover;
}

h2 {
  margin-bottom: 1em;
}

p {
  margin-bottom: 1em;
}
</style>