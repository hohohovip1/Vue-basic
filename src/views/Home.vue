<template>
    <div class="home">
        <h1>Home</h1>
        <PostList v-if="showPosts" :posts="posts" />
        <button @click="showPosts = !showPosts">Toggle posts</button>
        <button @click="posts.pop()">delete a post</button>
    </div>
</template>

<script>
import { ref } from "vue";
import PostList from "../components/PostList.vue";
export default {
    name: "Home",
    components: { PostList },
    setup() {
        const posts = ref([]);
        const error = ref(null);

        const load = async () => {
            try {
                let data = await fetch("http://localhost:3000/posts");
                if (!data.ok) {
                    throw Error("no data available");
                }
                posts.value = await data.json();
            } catch (err) {
                error.value = err.message;
                console.log(error.value);
            }
        };

        load();

        const showPosts = ref(true);
        return { posts, showPosts };
    },
};
</script>
