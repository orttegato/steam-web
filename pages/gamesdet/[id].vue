<template>
    <div class="body-detalle">
        <NuxtLink to="/comunity">
            <div class="boton-base">
                <BaseButton>Volver atrás</BaseButton>
            </div>
        </NuxtLink>
    <div v-if="data != null">
        <div class="introduccion-detalle">
            <img :src="data.background_image" :alt="data.name" class="img-detalle-comunidad">
            <main class="container">
                <h1>{{ data.name }}</h1>
                <p v-html="data.description">
                </p>
            </main>
        </div>
        <div class="introduccion-detalle-dos">
            <img :src="data.background_image" :alt="data.name" class="img-dos">
            <main class="data-container">
                <ul class="data-detalle">
                    <div class="el-detalle">
                        <p class="titulo">Rating:</p>
                        <p>{{ data.rating }}</p>
                    </div>
                    <div class="el-detalle">
                        <p class="titulo">Rating top:</p>
                        <p>{{ data.rating_top }}</p>
                    </div>
                    <div class="el-detalle">
                        <p class="titulo">Released:</p>
                        <p>{{ data.released }}</p>
                    </div>
                </ul>
            </main>
        </div>
    </div>
    </div>
</template>

<script setup>

import NavBarComunity from '@/components/local/NavBarComunity.vue';
const route = useRoute();
const { data } = useFetch(`https://api.rawg.io/api/games/${route.params.id}?key=3bf2278311dc4c4ab99bbe5ff644cf7f`);

</script>

<style lang="postcss">
.boton-base {
    width: 300px;
    padding-left: 50px;
}

.body-detalle {
    display: flex;
    flex-direction: column;
    padding-top: 70px;
    padding-bottom: 70px;
    gap: 80px;
    justify-content: center;
    width: 100%;
}

.introduccion-detalle {
    display: flex;
    flex-direction: row;

    .container {
        display: flex;
        flex-direction: column;
        padding: 40px;
        padding-top: 0;

        p {
            font-size: 10px;
            width: 85%;
        }
    }

    .img-detalle-comunidad {
        width: 800px;
        height: 500px;
        object-fit: cover;
        border-radius: 32px;
        border-top-left-radius: 0px;
        border-bottom-left-radius: 0px;
    }

}

.introduccion-detalle-dos {
    display: flex;
    flex-direction: row-reverse;

    .data-container {
        display: flex;
        flex-direction: column;
        padding: 40px;
        padding-top: 0;
        width: 900px;
        align-items: flex-start;

        .data-detalle {
            display: flex;
            flex-direction: column;
            gap: 5px;

            .el-detalle {
                display: flex;
                flex-direction: row;
                gap: 5px;
            }
        }

        p {
            font-size: 16px;
        }

        .titulo {
            color: #0047FF;
            font-weight: bold;
        }
    }

    .img-dos {
        width: 500px;
        height: 300px;
        object-fit: cover;
        border-radius: 32px;
        border-top-right-radius: 0px;
        border-bottom-right-radius: 0px;
    }

}

@media (max-width: 1024px) {

    .body-detalle {
        width: 100%;
        padding-top: 40px;
        gap: 30px;
    }

    .introduccion-detalle .img-detalle-comunidad {
        width: 400px;
        height: 300px;
        border-radius: 32px;
    }

    .introduccion-detalle {
        flex-direction: column;
        align-items: center;
        width: 100%;
        gap: 20px;
    }

    .introduccion-detalle .container p {
        font-size: 10px;
        width: 100%;
    }

    .introduccion-detalle-dos {
        flex-direction: column;
        padding-left: 50px;
    }

    .introduccion-detalle-dos .img-dos {
        width: 300px;
        height: 200px;
        border-radius: 32px;
    }

    .introduccion-detalle-dos .data-container {
        padding: 0;
        width: 100%;
        align-items: flex-start;
    }

    .introduccion-detalle-dos .data-container p {
        font-size: 12px;
    }

}
</style>