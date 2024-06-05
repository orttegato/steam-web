<template>
    <nav class="header">
        <div class="container-header">
            <div class="header-left">
                <NuxtLink to="/">
                    <img class="icono-normal" src="/public/logo.png" width="120px" alt="Logo">
                    <img class="icono-responsive" src="/public/solo.png">
                </NuxtLink>
            </div>
            <ul class="header-center">
                <li>
                    <NuxtLink to="/create">
                        <img class="icono-responsive" src="/public/create.png">
                        <p>SteamCreate</p>
                    </NuxtLink>
                </li>
                <li>
                    <NuxtLink to="/about">
                        <img class="icono-responsive" src="/public/tienda.png">
                        <p>Tienda</p>
                    </NuxtLink>
                </li>
                <li>
                    <NuxtLink to="/comunity">
                        <img class="icono-responsive" src="/public/comunidad.png">
                        <p>Comunidad</p>
                    </NuxtLink>
                </li>
            </ul>

            <button v-if="!logged && !iniciarmodalActive" @click="openIniciarModal">
                <p class="inicio">Iniciar sesión</p>
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
a {
    color: white;
    transition: color 0.3s ease;

    &:hover {
        color: #0047FF;
        font-weight: bold;
    }
}

.icono-responsive {
    display: none;
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

.inicio{
        font-size: 16px;
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

    p {
        font-size: 16px
    }

    p:hover {
        color: #0047FF
    }
}

ul {
    @apply flex p-4;

    li {
        @apply p-4;
    }
}

@media (max-width: 720px) {
    .icono-responsive {
        display: flex;
    }

    .icono-normal{
        display: none;
    }

    .header-center p {
        display: none;
    }

    .header-center{
        left: 115px;
    }

    li{
        padding: 5px;
    }

    .inicio{
        font-size: 12px;
}



}
</style>