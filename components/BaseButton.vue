<template>
    <button :class="buttonClasses" 
    @mouseover="isHovered = true" @mouseleave="isHovered = false" 
    @click="handleClick">
        <slot></slot>
    </button>
</template>

<script setup>
import { defineProps, computed, ref } from 'vue';

const props = defineProps({
    intent: {
        type: String,
        validator: (val) => ['primary', 'secondary', 'tertiary'].includes(val),
        default: 'primary',
    },
});

const isHovered = ref(false);

const buttonClasses = computed(() => {
    let backgroundColorClass = '';
    let hoverEffectClass = '';

    switch (props.intent) {
        case 'primary':
            backgroundColorClass = 'bg-indigo-600';
            hoverEffectClass = 'hover:bg-indigo-800'; 
            break;
        case 'secondary':
            backgroundColorClass = 'bg-gray-500';
            hoverEffectClass = 'hover:bg-gray-700'; 
            break;
        case 'tertiary':
            backgroundColorClass = 'bg-green-500';
            hoverEffectClass = 'hover:bg-green-700'; 
            break;

    }

    return `rounded-lg p-2 text-white ${backgroundColorClass} ${hoverEffectClass}`;
});

function handleClick() {
    console.log('Button clicked!');
    // You can emit an event or perform other actions on button click
}
</script>

<style scoped>

:root {
    --color-bg: #04050E;
    --color-primary: #0047FF;
    --color-secondary: #2B2B2B;
    --color-tertiary: #FFFFFF;
}

button {
    border: none;
    cursor: pointer;
    transition: background-color 0.3s ease;
}

button:focus {
    outline: none;
    /* Remove focus outline */
}
</style>