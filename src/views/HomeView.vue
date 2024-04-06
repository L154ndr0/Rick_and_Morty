<script setup>
import { ref } from 'vue';
import Card from "../components/Card.vue/"
let character = ref([])
let page = ref(1)

function nextPage(){
  page.value++
  loadCharacters()
}

function previousPage(){
  page.value--
  if(page.value<1){
    page.value=1
  }
  loadCharacters()
}

async function loadCharacters(){
  const response = await fetch(`http://rickandmortyapi.com/api/character?page=${page.value}`);
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

  <div class="flex justify-center m-4 space-x-4">
  <button class="bg-gray-300 rounded-x1 text-center" @click="previousPage" :disabled="page===1">Pagina anterior</button>
  <div>{{ page }}</div>
  <button class="bg-gray-300 rounded-x1 text-center" @click="nextPage">Siguiente pagina</button>
  </div>
  <div class="grid grid-cols-4 m-5">  
    <div v-for="personajes in character" :key="character.id">
      <Card :character="personajes"></Card>
    </div>
  </div>

</template>
