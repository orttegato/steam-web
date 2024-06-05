<template>
    <NuxtLink :to="`/gamesdet/${game.id}`">
        <article :class="['article', isLarge ? 'LargeArticle' : 'SmallArticle']">
            <h4>{{ game.name }}</h4>
            <div class="user-info-top">
                <div class="izq">
                    <svg data-v-4fa0a2a1="" xmlns="http://www.w3.org/2000/svg"
                        xmlns:xlink="http://www.w3.org/1999/xlink" aria-hidden="true" role="img" class="icon"
                        width="1.2em" height="1.2em" viewBox="0 0 256 256" style="color: white;">
                        <path fill="currentColor"
                            d="M230.92 212c-15.23-26.33-38.7-45.21-66.09-54.16a72 72 0 1 0-73.66 0c-27.39 8.94-50.86 27.82-66.09 54.16a8 8 0 1 0 13.85 8c18.84-32.56 52.14-52 89.07-52s70.23 19.44 89.07 52a8 8 0 1 0 13.85-8M72 96a56 56 0 1 1 56 56a56.06 56.06 0 0 1-56-56">
                        </path>
                    </svg>
                    <h5>Mateo</h5>
                </div>
                <p>Posted on {{ game.released }}</p>
            </div>
            <img :src="game.background_image" :alt="game.name" class="article-img">
            <div class="user-info-bottom">
                <p>A game made for artists</p>
                <img src="public/icons.png" alt="">
            </div>
        </article>
    </NuxtLink>
</template>

<script setup>
const props = defineProps({
    game: {
        type: Object,
        required: false
    },
    isLarge: {
        type: Boolean,
        default: false
    }
});
const { game } = props;

</script>

<style lang="postcss">
.article {
    background-color: #111216;
    padding-left: 20px;
    padding-right: 20px;
    padding-top: 40px;
    padding-bottom: 40px;
    margin-right: 15px;
    border-radius: 32px;


    .user-info-top {
        margin-top: 20px;
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        margin-bottom: 20px;
        align-items: baseline;

        .izq {
            display: flex;
            flex-direction: row;
            gap: 10px;
            align-items: center;
        }

        p {
            color: #787878;
        }
    }

    .user-info-bottom {
        margin-top: 20px;
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        align-items: center;
    }
}

.SmallArticle {
    width: 450px;

    .article-img {
        height: 350px;
        object-fit: cover;
    }
}

.LargeArticle {
    width: 800px;

    .article-img {
        height: 350px;
        width: 100%;
        object-fit: cover;
    }
}

@media (max-width: 1024px) {
    .article {
        padding-top: 20px;
        padding-bottom: 30px;
        width: 400px;
        height: 100%;
    }

    .SmallArticle .article-img {
        height: 300px;
        height: 250px;
        border-radius: 32px;
    }
}
</style>