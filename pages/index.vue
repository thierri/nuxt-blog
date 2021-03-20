<template>
    <div class="container">
        <div class="w-1/2 mx-auto">
            <h1 class="text-3xl">nuxt-blog-2</h1>
        </div>
        <div v-for="(post, index) in posts" :key="index">
            {{post.title}}
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            posts: [],
        };
    },
    created() {
        this.getPostData();
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
