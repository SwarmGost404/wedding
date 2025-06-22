<script setup lang="ts">
import { ref, onMounted } from 'vue';
import axios from 'axios';
import PolaroidCard from './PolaroidCard.vue';

interface Foto {
    url: string;
    caption: string;
    date: string
}

const foto = ref<Foto[]|null>(null)
const loading = ref<boolean>(true)

const fecthFoto = async () => {
    loading.value = true
    const response = await axios.get("/fotoVictor.json")
    if (response.status !== 200) {
        loading.value = false;
        throw new Error("Error status code: " + response.status);
    }
    foto.value = response.data
    loading.value = false;
    
}

onMounted(() => {
    fecthFoto()
})

</script>
<template>
    <div class="text-4xl mb-[100px]">Галерея</div>
    <div v-if="loading">
        <span class=" font-bold text-2xl">loading...</span>
    </div>
    <div
    class=" grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4 "
    v-else>
        <PolaroidCard
        v-for="photo in foto"
        :imageUrl="photo.url"
        :caption="photo.caption"
        :date="photo.date"
        />
    </div>
    <!-- <div class="text-4xl mb-[100px]">Злата</div> -->
</template>
<style>

</style>