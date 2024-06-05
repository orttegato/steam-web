<template>
    <div class="comunity-mercado">
        <section class="mercado-comunity" v-if="data != null">
            <div class="arriba">
                <h1>Comunidad</h1>
                <SearchBar></SearchBar>
            </div>
            <NavBarComunity></NavBarComunity>
            <p class="introduccion">Este el lugar ideal para que los jugadores se conecten, compartan y descubran
                contenido relacionado con sus juegos favoritos. Aquí, los usuarios pueden participar en foros de
                discusión, unirse a grupos, compartir capturas de pantalla y vídeos, y escribir reseñas de juegos.
                Además, es posible encontrar guías creadas por otros jugadores, seguir las últimas noticias y eventos de
                la comunidad, y participar en discusiones sobre estrategias y experiencias de juego. La Comunidad de
                Steam es un espacio dinámico y vibrante donde los jugadores de todo el mundo pueden interactuar y
                enriquecer su experiencia de juego.</p>
            <div class="mercado-menu">
                <h3 :class="{ active: currentView === 'popular' }" @click="currentView = 'popular'">Artículos populares</h3>
                <h3 :class="{ active: currentView === 'recent' }" @click="currentView = 'recent'">Recientes</h3>
            </div>
            <div class="mercado-container">
                <MercadoCard 
                    v-for="(game, index) in limitedResults" 
                    :key="index" 
                    :game="game" 
                    :reverseClass="currentView === 'recent' ? 'reverse' : ''" 
                />
            </div>
        </section>
    </div>
</template>

<script setup>
import { ref, computed } from 'vue';
import NavBarComunity from '@/components/local/NavBarComunity.vue';
import MercadoCard from '@/components/local/MercadoCard.vue';
const { data } = useFetch('https://api.rawg.io/api/games?key=3bf2278311dc4c4ab99bbe5ff644cf7f');

const currentView = ref('popular');

const setView = (view) => {
    currentView.value = view;
};


const limitedResults = computed(() => {
    if (data.value && data.value.results) {
        return data.value.results.slice(0, 10);
    }
    return [];
});
</script>

<style lang="postcss">
.comunity-mercado {
    display: flex;
    flex-direction: column;
    width: 100%;
}

.mercado-comunity {
    padding-top: 5rem;
    display: flex;
    flex-direction: column;
    align-items: center;

    h1 {
        align-self: self-start;
    }

    .arriba {
        display: flex;
        flex-direction: row;
        width: 90%;
        justify-content: space-between;
        align-items: center;
    }
}

.mercado-container {
    display: flex;
    flex-direction: column;
    width: 100%;
    align-items: center;
    justify-content: center;
    gap: 50px;
    padding: 50px;
    padding-right: 100px;
    padding-left: 100px;
}

.mercado-menu {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    width: 87%;
}

.mercado-menu h3 {
    padding: 0;
}

.mercado-menu h3:hover {
    color: #0047FF;
    cursor: pointer;
}

.mercado-menu h3.active {
    color: #0047FF;
}

@media (max-width: 1024px) {
    .mercado-container {
    gap: 60px;
    padding: 50px;
    padding-right: 20px;
    padding-left: 20px;
}

}


</style>
