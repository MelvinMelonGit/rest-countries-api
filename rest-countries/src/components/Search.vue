<script setup>
import { inject, ref } from 'vue'

const { searchCountry } = inject('countriesKey')

const searchValue = ref('')

</script>

<template>
  <div>
    <label for="name" class="visually-hidden">Name (4 to 8 characters):</label>

    <input type="text" id="name" name="name" size="10" placeholder="Search" @keyup="searchCountry(searchValue)" v-model="searchValue"/>
  </div>
</template>

<style scoped>
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