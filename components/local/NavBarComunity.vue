<template>
    <nav class="header-comunity">
            <img class="linea-fina" src="/public/Line 6.png">
            <ul class="container-comunity">
                <li>
                    <NuxtLink to="/comunity">
                        <img class="icono-responsive" src="/public/inicio.png">
                        <p>Inicio</p></NuxtLink>
                </li>
                <li>
                    <NuxtLink to="/artworks">
                        <img class="icono-responsive" src="/public/artworks.png">
                        <p>Artworks</p></NuxtLink>
                </li>
                <li>
                    <NuxtLink to="/mercado">
                        <img class="icono-responsive" src="/public/mercado.png">
                        <p>Mercado</p></NuxtLink>
                </li>
                <li>
                    <NuxtLink to="/retransmisiones">
                        <img class="icono-responsive" src="/public/retransmisiones.png">
                        <p>Retransmisiones</p></NuxtLink>
                </li>
            </ul>

            <img class="linea-fina" src="/public/Line 6.png">
    </nav>
</template>



<style lang="postcss">

.header-comunity {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 90%;
    ul{
        padding: 0px;
    }

    a {
    color: #787878;
    transition: color 0.3s ease;

    &:hover {
        color: #ffffff;
        font-weight: bold;
    }

    a:active {
        color: #ffffff;
        font-weight: bold;
    }

    p{
        font-size: 16px;
    }
}
}

.container-comunity{
    display: flex;
    width: 83%;
    justify-content: space-between;
}

.linea-fina {
    opacity: 70%;
    height: 0.5px;
    width: 100%;
}

ul {
    @apply flex p-4;

    li {
        @apply p-4;
    }
}

.subtitulo {
    font-size: 22px;
    font-weight: bold;
    align-self: flex-start;
    padding-left: 80px;
}



@media (max-width: 720px) {
    .container-comunity{
        align-items: center;
        p{
            display: none;
        }
    }

}
</style>