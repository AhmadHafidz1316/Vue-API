<template>
    <div class="container">
        <Blog :data="DataBlog"></Blog>
    </div>
</template>

<script>

import Blog from '@/components/beranda/Blog.vue';
import { Get } from '@/api/index.js';

export default {
    components : {
        Blog
    },
    data() {
        return {
            DataBlog : []
        }
    },

    async created () {
        const responseBlog = await Get('http://127.0.0.1:9000/api/blog');
        this.DataBlog = responseBlog.data.data;
    }
}
</script>