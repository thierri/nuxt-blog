<template>
    <div class="container">
        <div class="w-1/2 mx-auto my-20">
            <h1 class="text-3xl mb-10">nuxt-blog-2</h1>
            <div v-if="error" class="my-20">
                {{error}}
            </div>

            <nuxt-link class="text-gray-600" to="/">
                    Back to home
            </nuxt-link>

            <div
                v-if="post"
                class="my-10 text-gray-600"
            >
                <h1 class="text-5xl font-semibold mb-5">{{ post.title }}</h1>
                <p class="mb-5">
                    {{ post.abstract }}
                </p>
                <p class="text-gray-500">
                    {{ post.content }}
                </p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            post: null,
            error: null
        };
    },
    created() {
        this.getPostData();
    },
    methods: {
        getPostData() {
            this.$axios
                .$get(
                    "https://api.pistonapi.com/dope-blog-2/blog-post/" +
                        this.$route.params.article
                )
                .then((response) => {
                    this.post = response;
                })
                .catch((error) => {
                    this.error = "Ops, something wrong. Try again";
                });
        },
    },
};
</script>
