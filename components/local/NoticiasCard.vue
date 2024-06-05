<template>
    <div class="article-container">
        <div :class="{ 'image-left': imagePosition === 'left', 'image-right': imagePosition === 'right' }"
            class="article-noticias">
            <img class="img-noticias" :src="noticia.src" :alt="noticia.title">
            <div class="info-card">
                <div class="info-arriba">
                    <h1>{{ noticia.title }}</h1>
                    <p class="info">Tu plataforma definitiva para juegos y entretenimiento! Desde su lanzamiento en
                        2003, Steam se ha
                        convertido en el epicentro de la comunidad global de jugadores, ofreciendo una amplia variedad
                        de
                        juegos, contenido descargable, y funciones sociales para que disfrutes al máximo de tu
                        experiencia
                        de
                        juego</p>
                </div>
                <div class="info-abajo">
                    <p>Info 1</p>
                    <p>Info 2</p>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
const props = defineProps({
    noticia: {
        type: Object,
        required: false
    },
    imagen: {
        type: Object,
        required: false
    },
    imagePosition: {
        type: String,
        default: 'left' // Por defecto, la imagen está a la izquierda
    }
});
</script>

<style>
.article-container {
    display: flex;
    width: 100%;
    justify-content: center;
    padding-top: 50px;
    padding-bottom: 50px;
}

.article-noticias {
    display: flex;
    flex-direction: row;
    background-color: #111216;
    border-radius: 62px;
    width: 90%;
    height: 350px;
    gap: 50px;
    align-items: center;

    &.image-left {
        flex-direction: row;
    }

    &.image-right {
        flex-direction: row-reverse;
        justify-content: space-between;
        padding-left: 70px;
    }

    .img-noticias {
        width: 450px;
        height: 350px;
        border-radius: 62px;
        object-fit: cover;
    }

    .info {
        width: 500px;
    }

    .info-card {
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        height: 70%;

        .info-abajo {
            opacity: 50%;
        }
    }
}


@media (max-width: 1024px) {
    .article-noticias.image-left {
        flex-direction: column;
        gap: 0px;
        margin-bottom: 1rem;
        padding: 0px;
        height: 100%;
    }

    .article-noticias.image-right {
        flex-direction: column;
        gap: 0px;
        margin-bottom: 1rem;
        padding: 0px;
        height: 100%;
    }

    .article-noticias .info-card {
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        width: 90%;
        margin: 10px;
        padding: 10px;
    }

    .article-noticias .info {
    width: 100%;
}

}
</style>