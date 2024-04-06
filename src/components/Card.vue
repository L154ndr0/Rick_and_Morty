
<template>
    <div>
        <div>
            <img :src="character.image" alt="">
        </div>
        <div>
        <h3>{{ character.name }}</h3>
        </div>
    </div>
</template>

<script setup>
import { defineProps } from 'vue';

    const props = defineProps({
        character:{
        required:true,
        type: Object
        }
    })
</script>