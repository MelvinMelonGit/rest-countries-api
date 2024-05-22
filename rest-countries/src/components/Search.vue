<script setup>
import { inject, ref } from 'vue'

const { searchCountry } = inject('countriesKey')

const searchValue = ref('')

</script>

<template>
  <div>
    <label for="search-country" class="visually-hidden">Search for a country...</label>

    <input type="text" id="search-country" name="search-country" placeholder="Search for a country..." @keyup="searchCountry(searchValue)" v-model="searchValue"/>
  </div>
</template>

<style scoped>
input {
  box-shadow: 0px 10px 15px -3px rgba(0,0,0,0.1);
  border-radius: 0.3em;
  border: none;
  padding: 1.5em;
  margin-top: 3em;
}

.visually-hidden { 
    border: 0;
    padding: 0;
    margin: 0;
    position: absolute !important;
    height: 1px; 
    width: 1px;
    overflow: hidden;
    clip: rect(1px 1px 1px 1px); /* IE6, IE7 - a 0 height clip, off to the bottom right of the visible 1px box */
    clip: rect(1px, 1px, 1px, 1px); /*maybe deprecated but we need to support legacy browsers */
    clip-path: inset(50%); /*modern browsers, clip-path works inwards from each corner*/
    white-space: nowrap; /* added line to stop words getting smushed together (as they go onto seperate lines and some screen readers do not understand line feeds as a space */
}

</style>