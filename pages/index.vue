<template>
    <div class="container">
        <div class="w-1/2 mx-auto my-20">
            <h1 class="text-3xl font-semibold text-red-600">Super Blog</h1>
            <nuxt-link v-for="(post, index) in posts" :key="index" :to="post._id">
                <div
                    class="my-20 cursor-pointer text-gray-600 hover:text-gray-900"
                >
                    <h1 class="text-5xl font-semibold mb-5">
                        {{ post.title }}
                    </h1>
                    <p class="mb-5">
                        {{ post.abstract }}
                    </p>
                    <p class="text-red-500">Leia Mais</p>
                </div>
            </nuxt-link>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            posts: [
                {
                    _id: "3zpl477jpa",
                    title: 'O LIKE é fundamental para ajudar o canal',
                    abstract: 'Aqui deveria vir a descrição do artigo, mas como não tem nada também não vai ter uma descrição. Aqui deveria vir a descrição do artigo, mas como não tem nada também não vai ter uma descrição.'
                },
                {
                    _id: "3zpl477jpa",
                    title: 'Deixe seu like, não custa absolutamente nada',
                    abstract: 'Aqui deveria vir a descrição do artigo, mas como não tem nada também não vai ter uma descrição. Aqui deveria vir a descrição do artigo, mas como não tem nada também não vai ter uma descrição. '
                },
                {
                    _id: "3zpl477jpa",
                    title: 'Deu muito trabalho fazer esse vídeo, deixe seu like',
                    abstract: 'Aqui deveria vir a descrição do artigo, mas como não tem nada também não vai ter uma descrição. Aqui deveria vir a descrição do artigo, mas como não tem nada também não vai ter uma descrição.'
                },
            ],
        };
    },
    created() {
        //this.getPostData();
    },
    methods: {
        getPostData() {
            this.$axios
                .$get("https://api.pistonapi.com/dope-blog-2/blog-post")
                .then((response) => {
                    this.posts = response.data;
                });
        },
    },
};
</script>
