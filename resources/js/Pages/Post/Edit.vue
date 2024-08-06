<script>
import {Link} from '@inertiajs/vue3';
import MainLayout from "@/Layouts/MainLayout.vue";
export default {
    name: "Edit",

    components: {
        Link,
        MainLayout
    },

    props: [
        'post',
        'errors'
    ],

    data() {
      return {
          id: this.post.id,
          title: this.post.title,
          content: this.post.content
      }
    },

    methods: {
        update() {
            this.$inertia.patch(`/posts/${this.id}`, {title: this.title, content: this.content});
        }
    }
}
</script>

<template>
    <MainLayout>
        <h1 class="text-lg mb-8">Edit</h1>
        <div class="mb-8">
            <Link :href="route('post.index')" class="text-sm mb-8 text-sky-500">Back</Link>
        </div>
        <form @submit.prevent="update">
            <div class="mb-4">
                <input v-model="title" class="w-full rounded-full border-gray-300" type="text" placeholder="title">
                <div v-if="errors.title" class="text-red-600 text-sm">{{errors.title}}</div>
            </div>
            <div class="mb-4">
                <textarea v-model="content" class="w-full rounded-full border-gray-300" placeholder="content"></textarea>
                <div v-if="errors.content" class="text-red-600 text-sm">{{errors.content}}</div>
            </div>
            <div class="mb-4">
               <button class="ml-auto hover:bg-white hover:text-sky-500 border-sky-500 border bg-sky-500 rounded-full text-center text-white p-2 w-32" type="submit">Update</button>
            </div>
        </form>
    </MainLayout>
</template>

<style scoped>

</style>
