<template>
    <div class="container">
        <div class="w-1/2 mx-auto my-20">
            <h1 class="text-3xl">nuxt-blog-2</h1>
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
                    <p class="text-gray-500">Read more</p>
                </div>
            </nuxt-link>
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
