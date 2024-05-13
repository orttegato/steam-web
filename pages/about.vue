<template>
    <div>
        <HeaderImage :source="'/img2.jpg'"></HeaderImage>
        <h1>About</h1>
        <p>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Laudantium velit tempora reiciendis. Doloribus esse tempora exercitationem quibusdam dolorem voluptatem perspiciatis? Nisi ipsa ab hic quod delectus iusto, assumenda iure eos?</p>
        <section class="container cards-section">
        <ArticleCard v-for="(article, index) in articles" :key="index" :article="article">
        </ArticleCard>
    </section>
    
    </div>
</template>

<script setup>
const articles = ref([
    {
        id: 1,
        title: "Artículo 1",
        url: "https://fastly.picsum.photos/id/113/1024/300.jpg?hmac=TOHUmfAAmudYJQi9qnvSB7rExXTt5fGNfU7s_cE7mlA"
    },
    {
        id: 2,
        title: "Artículo 2",
        url: "https://fastly.picsum.photos/id/106/1024/300.jpg?hmac=sNtVy8TaufTArYC8gHv1QWIaPnd2jIJRX7ke19kXhXI"
    },
    {
        id: 3,
        title: "Artículo 3",
        url: "https://fastly.picsum.photos/id/107/1024/300.jpg?hmac=QzKvQQkCvQyedyOTP68TFXc9On4frOZ72h3cKy5DseY"
    },
    {
        id: 4,
        title: "Artículo 4",
        url: "https://fastly.picsum.photos/id/1032/1024/300.jpg?hmac=xahuD6APQyPNlzXgfC0vy2wLlbXEeoVJyQDBymJrVCc"
    }
])

</script>