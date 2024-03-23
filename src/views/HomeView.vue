<script setup>
import { ref } from 'vue';
import Card from "../components/Card.vue/"
let character = ref([])

async function loadCharacters(){
  const response = await fetch(`http://rickandmortyapi.com/api/character?page=1`);
  const data = await response.json()
  character.value = data.results
  console.log(data)
}
loadCharacters()

</script>

<template>
  <div class="flex justify-center mt-10">
    <h1 class="text-5xl">Personajes de Rick and Morty</h1>
  </div>

  <div v-for="Personajes in character" :key="character.id">
    {{ personajes.name }}

  </div>

<Card :character="character.value"></Card>

</template>
