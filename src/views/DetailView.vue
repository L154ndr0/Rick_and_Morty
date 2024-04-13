<template>
  <div v-if="character" class="about">

    <div class="bg-gray-300 grid grid-cols-2 rounded-full">
      <div class="m-20">
        <img class="rounded-xl console-center" :src="character.image" alt="">
      </div>
      <div class="flex flex-col items-center m-20">
        <h1 class="text-5xl font-bold">Name: {{ character.name }}</h1>

        <p class="text-2xl font-bold">Status: {{ character.status }}</p>
        <p class="text-2xl font-bold">Gender: {{ character.gender }}</p>
        <p class="text-2xl font-bold">location: {{ character.location.name }}</p>
        <p class="text-2xl font-bold">Origin: {{ character.origin.name }}</p>
        <p class="text-2xl font-bold">Species: {{ character.species }}</p>
      </div>
      
    </div>
  </div>
</template>

<script setup>
  import { useRoute } from 'vue-router';
  import { onMounted, ref } from "vue";

  const route = useRoute()
  const characterId = route.params.id

  const character = ref(null)

  onMounted (async() => {
  try{
    const response = await fetch(`http://rickandmortyapi.com/api/character/${characterId}`);
    const data = await response.json()
    character.value = data
    console.log(data)
  }
  catch{
  }
  })
  

</script>
