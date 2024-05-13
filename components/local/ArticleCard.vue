<template>
    <article>
    <img :src="article.url" :alt="article.title">
    <button>{{article.title}}</button>
</article>
</template>

<script setup>
    const props = defineProps({
        article: {
            type: Object,
            required: false
        }
    });
</script>

<style lang="postcss">
    article{
        img{
            width: 100%;
            object-fit: cover;
        }
        button{
            @apply p-5 bg-gray-200 w-full;
            text-align: center;
        }
    }
</style>