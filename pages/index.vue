<template>
    <div class="w-1/2 mx-auto my-20">
        <h1 class="text-3xl font-semibold text-red-600">{{tituloBlog}}</h1>
        <button v-on:click="carregarArtigos()">Carregar Artigos</button>
        
        <article v-for="artigo in artigos" class="my-20 text-gray-600">
            <h2 class="text-5xl font-semibold mb-5">
                {{artigo.title}}
            </h2>

            <p class="mb-5">
                {{artigo.abstract}}
            </p>

            <p class="text-red-500">Read more &rarr;</p>
        </article>
    </div>
</template>

<script>
export default {
    data() {
        return {
            tituloBlog: "Nuxt Blog",
            artigos: [],
        };
    },
    methods: {
        carregarArtigos() {
            this.$axios
                .get("https://api.pistonapi.com/dope-blog-2/blog-post")
                .then((dadosRetornados) => {
                    this.artigos = dadosRetornados.data.data;
                });
        },
    },
};
</script>

