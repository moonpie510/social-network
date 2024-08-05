<script>
import {Link} from '@inertiajs/vue3';
export default {
    name: "Index",
    components: {
        Link,
    },
}
</script>

<template>
    <div class="w-96 mx-auto pt-8">
        <h1 class="text-2xl mb-8">Posts</h1>
        <Link class="hover:bg-white hover:text-sky-500 border-sky-500 border bg-sky-500 rounded-full text-center text-white p-2 w-32">Add Post</Link>

    </div>
</template>

<style scoped>

</style>
