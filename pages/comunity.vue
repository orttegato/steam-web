import NavBarComunity from '~/components/local/NavBarComunity.vue';
<template>
    <div class="comunity-inicio">
        <section class="inicio-comunity" v-if="data != null">
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
            <h3 class="subtitulo">Post recientes</h3>
            <div class="articles-container">
                <div v-for="(gamePair, index) in pairedResults" :key="index" class="row">
                    <SmallArticle :game="gamePair[0]" :isLarge="isLargeCard(index, 0)"></SmallArticle>
                    <SmallArticle :game="gamePair[1]" :isLarge="isLargeCard(index, 1)"></SmallArticle>
                </div>
                <div v-for="(gamePair, index) in pairedResults" :key="index" class="row-small">
                    <SmallArticle :game="gamePair[0]"></SmallArticle>
                </div>
            </div>
        </section>
    </div>
</template>

<script setup>
import { ref, computed } from 'vue';
import NavBarComunity from '@/components/local/NavBarComunity.vue';
import SmallArticle from '@/components/local/SmallArticle.vue';
const { data } = useFetch('https://api.rawg.io/api/games?key=3bf2278311dc4c4ab99bbe5ff644cf7f');

const pairedResults = computed(() => {
    const pairs = [];
    const results = data.value.results.slice(0, 20); // Limitar las tarjetas

    for (let i = 0; i < results.length; i += 2) {
        const pair = [results[i], results[i + 1]];
        pairs.push(pair);
    }
    return pairs;
});

const isLargeCard = (rowIndex, cardPosition) => {
    const isEvenRow = rowIndex % 2 === 0;
    return (isEvenRow && cardPosition === 0) || (!isEvenRow && cardPosition === 1);
};

</script>

<style lang="postcss">
.comunity-inicio {
    display: flex;
    flex-direction: column;
    width: 100%;

}

.inicio-comunity {
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

.articles-container {
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

.row {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    gap: 50px;

}

.row-small{
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    gap: 50px;
    display: none;
}

.introduccion {
    width: 50%;
    align-self: flex-start;
    padding: 80px;
    padding-top: 30px;
    padding-bottom: 20px;
}

@media (max-width: 1024px) {
    .introduccion {
        width: 100%;
        padding: 30px;
    }

    .subtitulo {
        font-size: 20px;
        padding-left: 30px;
    }

    .row{
        display: none;
    }

    .row-small{
        display: flex;
    }


}
</style>