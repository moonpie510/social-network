<script>
import {Link} from '@inertiajs/vue3';
import MainLayout from "@/Layouts/MainLayout.vue";
export default {
    name: "Index",

    components: {
        Link,
        MainLayout
    },

    props: [
        'posts'
    ],

    methods: {
        deletePost(id) {
            this.$inertia.delete(`/posts/${id}`);
        }
    },

}
</script>

<template>
    <MainLayout>
        <h1 class="text-2xl mb-8">Posts</h1>
        <div class="mb-8">
            <Link :href="route('post.create')" class="hover:bg-white hover:text-sky-500 border-sky-500 border bg-sky-500 rounded-full text-center text-white p-2 w-32">Add Post</Link>
        </div>
        <div v-if="posts">
            <div v-for="post in posts" class="mt-8 pt-8 border-t border-gray-300">
                <div>id: {{post.id}}</div>
                <div>title: {{post.title}}</div>
                <div>content: {{post.content}}</div>
                <div class="text-sm text-right">{{post.date}}</div>
                <div class="text-sm text-right">
                    <Link :href="route('post.show', post.id)" class="text-sky-500">Show</Link>
                </div>
                <div class="text-sm text-right">
                    <Link :href="route('post.edit', post.id)" class="text-sky-500">Edit</Link>
                </div>
                <div class="text-sm text-right">
                    <p @click.prevent="deletePost(post.id)" class="cursor-pointer text-red-500">Delete</p>
                </div>
            </div>
        </div>
    </MainLayout>
</template>

<style scoped>

</style>
