<template>
    <div class="search-bar">
        <img src="/public/Search.png">
        <input 
        type="text" 
        v-model="searchTerm" 
        @input="handleInput" 
        placeholder="Search something..." 
        class="search-input" />
    </div>
</template>

<script setup>
import { ref } from 'vue';

const searchTerm = ref('');

function handleInput(event) {
    searchTerm.value = event.target.value;
}

function search() {
    // Implement your search functionality here
    console.log('Searching for:', searchTerm.value);
}
</script>

<style scoped>
.search-bar {
    display: flex;
    align-items: center;
    justify-content: space-between;
    background-color: #C5CDD7;
    padding: 6px;
    font-size: 16px;
    border-radius: 8px;
    width: 250px;
    height: 45px;
    gap: 5px;

    img{
        width: 28px;
    }

    .search-input{
        background-color: #C5CDD7;
    }
}


</style>