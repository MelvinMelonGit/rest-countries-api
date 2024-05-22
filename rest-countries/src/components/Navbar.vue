<script setup>
import { computed, ref } from 'vue'

const title = ref('Where in the world?')

const colourScheme = ref(false)

const colourMode = computed(() => {
  return colourScheme.value ? 'Dark Mode' : 'Light Mode'
})

function toggleColour() {
  colourScheme.value = !colourScheme.value
}

</script>

<template>
  <nav :class="{ dark: colourScheme }">
    <div>
      <h1>{{ title }}</h1>
      <p @click="toggleColour">{{ colourMode }}</p>
    </div>
  </nav>
</template>

<style scoped>
nav {
  padding: 2em 0;
  box-shadow: 0px 10px 15px -3px rgba(0,0,0,0.1);
  background-color: hsl(0, 0%, 100%);
  color: hsl(207, 26%, 17%);
}

nav.dark {
  background-color: hsl(207, 26%, 17%);
  color: hsl(0, 0%, 100%);
}

div {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 80%;
  margin: 0 auto;
}

h1, p {
  font-weight: 800;
  font-style: normal;
}

p {
  cursor: pointer;
}
</style>