<template>
    <div class="comunity-artworks">
        <section class="artworks-comunity">
            <div class="arriba">
                <h1>Comunidad</h1>
                <SearchBar></SearchBar>
            </div>
            <NavBarComunity></NavBarComunity>
            <p class="introduccion">
                Este el lugar ideal para que los jugadores se conecten, compartan y descubran
                contenido relacionado con sus juegos favoritos. Aquí, los usuarios pueden participar en foros de
                discusión, unirse a grupos, compartir capturas de pantalla y vídeos, y escribir reseñas de juegos.
                Además, es posible encontrar guías creadas por otros jugadores, seguir las últimas noticias y eventos de
                la comunidad, y participar en discusiones sobre estrategias y experiencias de juego. La Comunidad de
                Steam es un espacio dinámico y vibrante donde los jugadores de todo el mundo pueden interactuar y
                enriquecer su experiencia de juego.
            </p>
        </section>
    </div>

    <section>
        <h3 class="subtitulo">En directo ahora</h3>
        <RetransmisionesCard imageSrc="/directo1.png"></RetransmisionesCard>
        <RetransmisionesCard imageSrc="/directo2.png"></RetransmisionesCard>
        <RetransmisionesCard imageSrc="/directo3.png"></RetransmisionesCard>
    </section>
</template>

<script setup>
import RetransmisionesCard from '@/components/local/RetransmisionesCard.vue';
import NavBarComunity from '@/components/local/NavBarComunity.vue';
</script>

<style lang="postcss">
.subtitulo{
    
    font-weight: bold;
}
</style>
