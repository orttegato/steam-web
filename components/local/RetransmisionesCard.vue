<template>
    <div class="retransmisiones">
        <div class="retransmisiones-container">
            <img class="img-retransmisiones" :src="imageSrc" alt="img-directo">
            <div class="info-retransmisiones">
                <img class="img-user" src="public/retr.png" alt="">
                <h5>Jugando a Red Dead Redemption!</h5>
                <p>Illojuan</p>
            </div>
        </div>
    </div>
</template>

<script setup>
const props = defineProps({
    imageSrc: {
        type: String,
        required: true
    }
});
</script>

<style lang="postcss">
.retransmisiones {
    width: 100%;
    display: flex;
    justify-content: center;
    padding: 20px;

    .retransmisiones-container {
        display: flex;
        flex-direction: column;
        justify-content: center;
        margin-top: 40px;
        border-radius: 32px;
        width: 1200px;
        justify-content: space-between;
        background-color: #111216;

        .img-retransmisiones {
            width: 1200px;
            height: 400px;
            object-fit: cover;
            border-radius: 32px;
        }

        .info-retransmisiones {
            display: flex;
            flex-direction: row;
            margin-top: 20px;
            justify-content: space-between;
            align-items: center;
            padding: 30px;
            padding-top: 10px;
            gap: 20px;

            .img-user {
                width: 50px;
                height: 50px;
                display: flex;
                align-self: center;
                border-radius: 1000px;
            }
        }
    }
}
</style>
