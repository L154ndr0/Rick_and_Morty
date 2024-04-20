
<template>
    <div class="flex flex-col overflow-hidden rounded-xl shadow-xl">
        <div>
            <img :src="character.image" alt="">
        </div>
        <div>
        <h3>{{ character.name }}</h3>
        </div>
    </div>
</template>

<script setup>

    const props = defineProps({
        character:{
        required:true,
        type: Object
        }
    })

</script>