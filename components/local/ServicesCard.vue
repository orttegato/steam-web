<template>
    <div class="service-container">
        <div :class="{ 'image-left': imagePosition === 'left', 'image-right': imagePosition === 'right' }"
            class="service-noticias">
            <img :src="service.src" :alt="service.title">
            <div class="info-card">
                <div class="info-arriba">
                    <h1>{{ service.title }}</h1>
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
                    <BaseButton>Ir a la web</BaseButton>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
const props = defineProps({
    service: {
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
.service-container {
    display: flex;
    width: 100%;
    padding-bottom: 50px;
}

.service-noticias {
    display: flex;
    flex-direction: row;
    height: 350px;
    gap: 50px;
    justify-content: space-between;

    &.image-left {
        flex-direction: row;
        gap: 100px;

        img {
            border-top-right-radius: 62px;
            border-bottom-right-radius: 62px;
        }
    }

    &.image-right {
        flex-direction: row-reverse;

        img {
            border-top-left-radius: 62px;
            border-bottom-left-radius: 62px;
        }
    }

    img {
        width: 700px;
        object-fit: cover;
    }

    .info {
        width: 50%;
    }

    .info-card {
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        height: 100%;

    }
}


@media (max-width: 1024px) {

    .servicios{
        display: flex;
        flex-direction: column;
        gap: 50px;
    }

    .service-container {
        padding-bottom: 120px;
    }

    .service-noticias.image-left {
        flex-direction: column;
        gap: 20px;
    }

    .service-noticias.image-right {
        flex-direction: column;
        gap: 20px;
    }

    .service-noticias img {
        width: 500px;
    }

    .service-noticias .info-card {
    padding: 20px;
    gap: 20px;
}

.service-noticias .info {
    width: 90%;
}

}
</style>