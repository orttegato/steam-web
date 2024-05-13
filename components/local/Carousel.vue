<template>
    <div class="carousel">
        <div class="slide" :class="{ active: currentIndex === index }" v-for="(image, index) in images" :key="index">
            <img :src="image" alt="Slide" />
        </div>
    </div>
    <div class="buttons">
        <BaseButton intent="secondary" @click="prevSlide">Previous</BaseButton>
        <BaseButton intent="secondary" @click="nextSlide">Next</BaseButton>
    </div>
</template>

<script setup>
import { ref } from 'vue';

const images = [
    'Rectangle 8.png',
    'Rectangle 9.png',
    'Rectangle 70.png',

];

const currentIndex = ref(0);

function nextSlide() {
    currentIndex.value = (currentIndex.value + 1) % images.length;
}

function prevSlide() {
    currentIndex.value = (currentIndex.value - 1 + images.length) % images.length;
}
</script>

<style scoped>
.carousel {
    width: 1400px;
    height: 520px;
    position: relative;
    margin: auto;
    display: flex;
    justify-content: center;
}

.buttons{
    width: 1400px;
    display: flex;
    justify-content: center;
    gap: 50px;
}

.slide {
    position: absolute;
    opacity: 0;
    transition: opacity 0.5s ease;

    img {
        width: 1400px;
        height: 500px;
        object-fit: cover;
        border-radius: 64px;
    }
}

.slide.active {
    opacity: 1;
}
</style>