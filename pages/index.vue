<template>
    <div class="body">
        <section class="inicio">
            <div class="text-inicio">
                <h1>Bienvenido a Steam!</h1>
                <p>Tu plataforma definitiva para juegos y entretenimiento! Desde su lanzamiento en 2003, Steam se ha
                    convertido en el epicentro de la comunidad global de jugadores, ofreciendo una amplia variedad de
                    juegos, contenido descargable, y funciones sociales para que disfrutes al máximo de tu experiencia
                    de
                    juego</p>
            </div>
            <div class="carousel-container">
                <Carousel></Carousel>
            </div>
        </section>

        <div class="noticias-container">
            <article class="noticias">
                <div class="text-noticias">
                    <h1>Noticias</h1>
                    <p>Tu plataforma definitiva para juegos y entretenimiento! Desde su lanzamiento en 2003, Steam se ha
                        convertido en el epicentro de la comunidad global de jugadores, ofreciendo una amplia variedad
                        de
                        juegos, contenido descargable, y funciones sociales para que disfrutes al máximo de tu
                        experiencia
                        de
                        juego</p>
                </div>
                <SearchBar></SearchBar>
            </article>

            <div class="separador-container">
                <div class="separador-noticias">
                    <h3>Próximamente</h3>
                    <img src="/public/Line 6.png">
                </div>
            </div>
            <div class="noticia-container">
                <NoticiasCard v-if="showSingleCard" :noticia="noticias[0]" :imagePosition="'left'">
                </NoticiasCard>

            </div>
            <div class="separador-container">
                <div class="separador-noticias">
                    <h3>Hoy</h3>
                    <img src="/public/Line 6.png">
                </div>
            </div>

            <div class="noticia-container">
                <NoticiasCard v-for="(noticia, index) in noticias.slice(1, 3)" :key="index" :noticia="noticia"
                    :imagePosition="'right'">
                </NoticiasCard>
            </div>

            <div class="boton">
                <BaseButton>Ver más</BaseButton>
            </div>
        </div>

        <div class="servicios-container">
            <article class="servicios">
                <h1 class="indice">Servicios</h1>
                <ServicesCard v-for="(service, index) in services" :key="index" :service="service"
                    :imagePosition="servicesConfig[index].imagePosition">
                </ServicesCard>
            </article>
        </div>
    </div>

</template>




<script setup>
import Carousel from '@/components/local/Carousel.vue';
import NoticiasCard from '@/components/local/NoticiasCard.vue';
import ServicesCard from '@/components/local/ServicesCard.vue';
import { ref } from 'vue'


const { data } = useFetch('https://api.rawg.io/api/games?key=3bf2278311dc4c4ab99bbe5ff644cf7f');


const noticias = ref([
    {
        id: 1,
        title: "Noticia 1",
        src: "/Rectangle 9.png"
    },
    {
        id: 2,
        title: "Noticia 2",
        src: "Rectangle 70.png"
    },
    {
        id: 3,
        title: "Noticia 3",
        src: "Rectangle 970.png"
    },
])
// Variable para controlar el número de tarjetas a mostrar
const showSingleCard = ref(true); // Mostrar solo una tarjeta la primera vez

// Lógica para determinar imagePosition dinámicamente
const imagePosition = computed(() => {
    return showSingleCard.value ? 'left' : 'right';
});

const services = ref([
    {
        id: 1,
        title: "Valve Index",
        src: "Rectangle 7.png"
    },
    {
        id: 2,
        title: "Steam Deck",
        src: "Rectangle 1.png"
    },
])

const servicesConfig = ref([
    {
        imagePosition: 'left'
    },
    {
        imagePosition: 'right'
    }
]);

</script>

<style lang="postcss">
body {
    border: 1px red;
}

p {
    font-size: 12px;
}

h1 {
    font-size: 60px;
    font-weight: bolder;
}


.inicio {
    display: flex;
    flex-direction: column;
    width: 100%;
    align-items: center;

    h1 {
        width: 800px;
    }


    .text-inicio {
        display: flex;
        flex-direction: row;
        width: 100%;
        justify-content: space-between;
        align-items: flex-end;
        gap: 10px;
        padding: 60px;
        padding-left: 100px;
        padding-right: 100px;

        p {
            width: 300px;
        }
    }
}

.noticias {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: flex-start;
    padding: 100px;
    padding-bottom: 50px;


    .text-noticias {
        display: flex;
        flex-direction: row;
        width: 50%;
        justify-content: space-between;
        align-items: flex-end;
        gap: 10px;

        h1 {
            width: 50px;
        }

        p {
            width: 300px;
        }
    }
}


.cards-section {
    display: flex;
    justify-content: space-between;
}

.separador-container {
    display: flex;
    width: 100%;
    justify-content: center;

    .separador-noticias {
        display: flex;
        flex-direction: row;
        width: 87%;
        justify-content: space-between;
        align-items: center;
        gap: 50px;

        img {
            width: 1200px;
            height: 2px;
        }

    }
}

.boton {
    padding-left: 80px;
}

.servicios-container {
    display: flex;
    flex-direction: column;
    width: 100%;
    align-items: center;
    padding-top: 50px;

    .indice {
        padding-left: 70px;
    }
}

@media (max-width: 1024px) {

    .body{
        overflow: hidden;
    }
    h1 {
        font-size: 20px;
        font-weight: bolder;
    }

    p {
        font-size: 10px;
    }

    .noticias{
        padding: 20px;
        flex-direction: column;

    }

    .noticias .text-noticias{
        width: 85%;
        justify-content: center;
        flex-direction: column;
        align-items: flex-start;
    }

    .inicio .text-inicio {
        width: 85%;
        justify-content: center;
        flex-direction: column;
        align-items: flex-start;
        padding: 20px;;
    }


}
</style>