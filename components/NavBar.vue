<template>
    <nav class="header">
        <div class="container-header">
            <div class="header-left">
                <img src="/public/logo.png" width="120px">
            </div>
            <ul class="header-center">
                <li>
                    <NuxtLink to="/">SteamCreate</NuxtLink>
                </li>
                <li>
                    <NuxtLink to="/about">Tienda</NuxtLink>
                </li>
                <li>
                    <NuxtLink to="/">Comunidad</NuxtLink>
                </li>
                <li>
                    <NuxtLink to="/about">Soporte</NuxtLink>
                </li>
            </ul>

            <button v-if="!logged && !iniciarmodalActive" @click="openIniciarModal">
                Iniciar sesión
            </button>
            <div v-else class="user" @click="logout">
                <Icon name="ph:user" size="1.2em" color="white" />
            </div>

            <IniciarModal v-if="iniciarmodalActive" @close-modal="closeIniciarModal" />

        </div>
        <img class="linea-fina" src="/public/Line 6.png">

    </nav>
</template>



<script setup>

import { ref } from 'vue'
import IniciarModal from './IniciarModal.vue';


const iniciarmodalActive = ref(false);
const logged = ref(false);


const openIniciarModal = () => {
    iniciarmodalActive.value = true;
};

const closeIniciarModal = (e) => {
    iniciarmodalActive.value = false;
    if (e == "logged") {
        logged.value = true;
    }
}

const logout = () => {
    logged.value = false;
};

</script>

<style lang="postcss">
/* Estilo para NuxtLink */
a {
    color: white;
    /* Color por defecto del texto */
    transition: color 0.3s ease;
    /* Transición suave del color */

    /* Cambia el color al hacer hover */
    &:hover {
        color: #0047FF;
        /* Color azul al hacer hover */
    }
}

.header {
    display: flex;
    flex-direction: column;
    align-items: center;
    background-color: #04050E;
    z-index: 9999;

}

.linea-fina {
    opacity: 70%;
    height: 0.5px;
    width: 100%;
}

.container-header {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
    width: 100%;
    padding: 20px;
    padding-left: 40px;
    padding-right: 40px;
}

.header-center {
    position: absolute;
    left: 550px;
}

ul {
    @apply flex p-4;

    li {
        @apply p-4;
    }
}
</style>