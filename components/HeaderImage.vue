

<template>
    <img class="header-image" :src="source" alt="imagen de prueba">
</template>

<style lang="postcss">
.header-image{
    padding: 20px;
    width: 90%;
    height: 600px;
    object-fit: cover;
    border-radius: 32px;
}
</style>

<script setup>
    const props = defineProps({
        source: {
            type: String,
            required: false
        },
    });
    const { source } = props;
</script>