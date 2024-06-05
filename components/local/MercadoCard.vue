<template>
    <div :class="['mercado', reverseClass]">
        <img :src="game.background_image" :alt="game.name" class="mercado-img">
        <div class="mercado-title">
            <h2>{{ game.name }}</h2>
            <p>{{ game.name }}</p>
        </div>
        <div class="price-tag">
            <h2>25.99$</h2>
        </div>
    </div>
</template>

<script setup>
const props = defineProps({
    game: {
        type: Object,
        required: true
    },
    reverseClass: {
        type: String,
        default: ''
    }
});
</script>

<style lang="postcss">
.mercado {
    display: flex;
    flex-direction: row;
    width: 100%;
    height: 250px;
    justify-content: space-between;
    background-color: #111216;
    border-radius: 32px;
    align-items: center;
    padding-right: 50px;
}

.mercado.reverse {
    flex-direction: row-reverse;
    padding-right: 0px;
    padding-left: 50px;
}

.mercado-img {
    height: 100%;
    border-top-left-radius: 32px;
    border-bottom-left-radius: 32px;
    object-fit: cover;
}

.mercado-title {
    flex-grow: 1;
    padding: 0 20px;
    display: flex;
    flex-direction: column;
    justify-content: center;
}

.price-tag {
    display: flex;
    align-items: center;
    padding-right: 20px;
}


@media (max-width: 1024px) {
    .mercado {
    flex-direction: column;
    padding-right: 0px;
    gap: 5px;
    height: 100%;
    padding-bottom: 20px;
}

.mercado-img {
    border-radius: 32px;
}

.mercado-title{
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
    width: 100%;
}

.price-tag {
    justify-content: flex-end;
    width: 100%;
}

.mercado.reverse {
    flex-direction: column;
    padding-right: 0px;
    gap: 5px;
    height: 100%;
    padding-bottom: 20px;
    padding-left: 0px;
}

}
</style>
