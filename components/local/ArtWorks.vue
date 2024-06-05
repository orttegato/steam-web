<template>
    <div :class="['card', cardSize]">
        <img :src="game.background_image" :alt="game.name" />
        <div class="content">
            <div class="top">
                <p class="author">Mateo</p>
                <p class="date">Posted on {{ game.released }}</p>
            </div>
            <div class="middle">
                <h2><b>{{ game.name }}</b></h2>
                <p class="info-art">Los Sueños. El LSPD informa de un gran aumento de los delitos en toda el área metropolitana de Los
                    Sueños. Los SWAT tratan de solventar situaciones de alto riesgo como tomas de rehenes, amenazas de
                    bomba y sospechosos atrincherados, entre otros.</p>
            </div>
            <div class="bottom">
                <p>Rating: {{ game.rating }}</p>
                <p>Stats: {{ game.rating_top }}</p>
            </div>
        </div>
    </div>
</template>

<script setup>
import { defineProps } from 'vue';

const props = defineProps({
    game: {
        type: Object,
        required: false
    },
    cardSize: {
        type: String,
        default: ''
    }
});

const { game } = props;
</script>

<style lang="postcss">
.card {
    background: #04050E;
    color: white;
    margin: 20px;
    border-radius: 32px;
    overflow: hidden;
    display: flex;
    flex-direction: column;
    height: 300px;
}

/*CARD GRANDE*/

.card.large {
    flex-direction: row;
    height: 300px;
    width: 1200px;

    img {
        height: 300px;
        width: 1000px;
        border-radius: 32px;
        object-fit: cover;
    }

    .bottom{
        gap: 20px;
    }
}

/*CARD PEQUEÑA*/

.card.small {
    flex-direction: row;
    height: 300px;
    width: 900px;

    img {
        width: 300px;
        height: 300px;
        border-radius: 32px;
        object-fit: cover;
    }

    .bottom{
        gap: 20px;
    }
}

/*CARD SOLO IMG*/

.card.full-image {
    flex-direction: column;
    width: 1320px;
    height: 365px;

    img {
        width: 100%;
        height: 300px;
        border-radius: 32px;
        object-fit: cover;
    }

    .content {
        padding: 30px;
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        width: 100%;
        align-items: center;
    }

    .middle, .bottom {
        width: 33%;
        display: flex;
        flex-direction: row;
        justify-content: space-between;
    }

    .top{
        display: flex;
        flex-direction: column;
    }

    .bottom{
        width: 150px;
    }

    .info-art{
        display: none;
    }
}

/*CARD SOLO IMG MEDIANA*/

.card.full-image-medium {
    flex-direction: column;
    width: 500px;
    height: 900px;

    img {
        width: 100%;
        height: 700px;
        border-radius: 32px;
        object-fit: cover;
    }

    .content {
        padding: 30px;
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        width: 100%;
        align-items: center;
    }

    .middle, .bottom {
        width: 40%;
        display: flex;
        flex-direction: row;
        justify-content: space-between;
    }

    .top{
        display: flex;
        flex-direction: column;
    }

    .bottom{
        width: 150px;
    }

    .info-art{
        display: none;
    }
}

/*CARD SOLO IMG SMALL*/

.card.full-image-small {
    flex-direction: column;
    width: 700px;
    height: 360px;
    padding: 0;

    img {
        height: 300px;
        border-radius: 32px;
        object-fit: cover;
    }

    .content {
        padding: 20px;
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        width: 100%;
        align-items: center;
    }

    .middle, .bottom {
        width: 33%;
        display: flex;
        flex-direction: row;
        justify-content: space-between;
    }

    .top{
        display: flex;
        flex-direction: column;
    }

    .bottom{
        width: 150px;
    }

    .info-art{
        display: none;
    }
}

.content {
    width: 500px;
    padding: 30px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;

    .top {
        display: flex;
        flex-direction: row;
        justify-content: space-between;

        .date {
            color: #787878;
            ;
        }
    }

    .bottom {
        display: flex;
        flex-direction: row;
    }

    .middle{
        display: flex;
        flex-direction: column;
        gap: 12px;
        p{
            font-size: 10px;
        }
    }
}


@media (max-width: 1024px) {
    .card.full-image-small{
        flex-direction: column;
    width: 400px;
    height: 360px;
    padding: 0;
    }

    .card.full-image-small .bottom {
    display: none;
}
}
</style>