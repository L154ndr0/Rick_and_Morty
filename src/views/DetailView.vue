<template>
  <div v-if="character" class="about">

    <div class="grid grid-cols-1 lg:grid-cols-2 h-screen">
      <div class="m-12">
        <img class="h-full w-full rounded-3xl" :src="character.image" alt="">
      </div>
      <div class="flex flex-col items-center justify-center m-12 space-y-8">
        <h1 class="text-5xl font-bold">{{ character.name }}</h1>
         
        <div class="flex">
          <Icon class="text-3xl" icon="game-icons:half-dead" /><p class="text-2xl font-bold">Status: {{ character.status }}</p>
        </div>
        <div class="flex">
          <Icon class="text-3xl" icon="icons8:gender" /><p class="text-2xl font-bold">Gender: {{ character.gender }}</p>
        </div>
        <div class="flex">
          <Icon class="text-3xl" icon="carbon:location-filled" /><p class="text-2xl font-bold">location: {{ character.location.name }}</p>
        </div>
        <div class="flex">
          <Icon class="text-3xl m-1" icon="subway:world-1" /><p class="text-2xl font-bold">Origin: {{ character.origin.name }}</p>
        </div>
        <div class="flex">
          <Icon class="text-3xl" icon="ph:person-fill" /><p class="text-2xl font-bold">Species: {{ character.species }}</p>
        </div>
        
      </div>
      <Icon icon="mdi-light:home" />
    </div>
  </div>
</template>

<script setup>
  import { useRoute } from 'vue-router';
  import { onMounted, ref } from "vue";
  import { Icon } from '@iconify/vue';

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
