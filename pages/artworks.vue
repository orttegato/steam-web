<template>
    <div class="comunity-artworks">
        <section class="artworks-comunity" v-if="data != null">
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

            <h3 class="subtitulo">Más destacados</h3>
            <div class="articles-artworks">

                <div class="articles-pequeño">
                    <div v-for="(game, index) in limitedResults.slice(0, 4)" :key="index">
                        <ArtWorks :game="game" cardSize="full-image-small"></ArtWorks>
                    </div>
                </div>

                <div class="article-grande">
                    <div v-for="(game, index) in limitedResults" :key="index">
                        <ArtWorks :game="game" :cardSize="getCardSize(index)"></ArtWorks>
                    </div>
                </div>
            </div>

            <h3 class="subtitulo">Según tus juegos</h3>

            <div class="articles-pequeño">
                    <div v-for="(game, index) in limitedResults.slice(0, 8)" :key="index">
                        <ArtWorks :game="game" cardSize="full-image-small"></ArtWorks>
                    </div>
                </div>

            <div class="article-grande">
                <section class="single-card-section">
                    <ArtWorks :game="featuredGame" cardSize="full-image"></ArtWorks>
                </section>
            </div>
            <div class="article-grande">
                <div class="articles-artworks-complex">

                    <div v-for="(game, index) in limitedResultsSecondary" :key="index">
                        <ArtWorks :game="game" :cardSize="getCardSizeSecondary(index)"></ArtWorks>
                    </div>
                    <div class="column">
                        <div v-for="(game, index) in limitedResultsTertiary" :key="index">
                            <ArtWorks :game="game" :cardSize="getCardSizeTertiary(index)"></ArtWorks>
                        </div>
                    </div>
                </div>
            </div>

        </section>
    </div>
</template>

<script setup>
import { ref, computed } from 'vue';
import ArtWorks from '@/components/local/ArtWorks.vue';
import NavBarComunity from '@/components/local/NavBarComunity.vue';
const { data } = useFetch('https://api.rawg.io/api/games?key=3bf2278311dc4c4ab99bbe5ff644cf7f');

const randomIndexes = computed(() => {
    if (data.value && data.value.results) {
        const resultsCount = data.value.results.length;
        const maxIndexes = Math.min(resultsCount, 4); // Tomar hasta un máximo de 4 índices aleatorios
        const indexes = [];
        for (let i = 0; i < maxIndexes; i++) {
            indexes.push(Math.floor(Math.random() * resultsCount));
        }
        return indexes;
    }
    return [];
});

const limitedResults = computed(() => {
    if (data.value && data.value.results) {
        return randomIndexes.value.map(index => data.value.results[index]);
    }
    return [];
});

const getCardSize = (index) => {
    const sizes = ['large', 'small', 'large', 'small'];
    return sizes[index % sizes.length];
};

const featuredGame = computed(() => {
    if (data.value && data.value.results) {
        return data.value.results[7];
    }
    return null;
});

const limitedResultsSecondary = computed(() => {
    if (data.value && data.value.results) {
        return data.value.results.slice(0, 1);
    }
    return [];
});

const getCardSizeSecondary = (index) => {
    const sizesSecondary = ['full-image-medium'];
    return sizesSecondary[index % sizesSecondary.length];
};

const randomIndexesTertiary = computed(() => {
    if (data.value && data.value.results) {
        const resultsCount = data.value.results.length;
        const maxIndexes = Math.min(resultsCount, 2);
        const indexes = [];
        for (let i = 0; i < maxIndexes; i++) {
            indexes.push(Math.floor(Math.random() * resultsCount));
        }
        return indexes;
    }
    return [];
});

const limitedResultsTertiary = computed(() => {
    if (data.value && data.value.results) {
        return randomIndexesTertiary.value.map(index => data.value.results[index]);
    }
    return [];
});

const getCardSizeTertiary = (index) => {
    const sizesSecondary = ['full-image-small', 'full-image-small']; // Nueva constante de tamaños
    return sizesSecondary[index % sizesSecondary.length];
};

</script>



<style lang="postcss">
.comunity-artworks {
    display: flex;
    flex-direction: column;
    width: 100%;
    overflow: hidden;

}

.articles-pequeño {
    display: none;
}

.artworks-comunity {
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

.articles-artworks {
    display: flex;
    flex-direction: column;
    width: 100%;
    align-items: flex-start;
    gap: 50px;
    padding: 50px;
    padding-right: 71px;
    padding-left: 71px;
}

.articles-artworks-complex {
    display: flex;
    flex-direction: row;
    width: 100%;
    align-items: flex-start;
    justify-content: space-between;
    gap: 50px;
    padding: 50px;
    padding-right: 71px;
    padding-left: 71px;

    .column {
        display: flex;
        flex-direction: column;
        gap: 20px;
    }
}


@media (max-width: 1024px) {

    .articles-artworks {
    align-items: center;
    width: 100%;
    gap: 50px;
    padding: 50px;
    padding-right: 20px;
    padding-left: 20px;
}
    .article-grande {
        display: none;
    }

    .articles-pequeño {
        display: flex;
        flex-direction: column;
    }

}
</style>