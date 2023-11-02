<template>
    <div class="container">
      <Beranda :data="DataHome"></Beranda>
      <Service :data="DataLayanan"></Service>
    </div>
  </template>
  <script>
  import Beranda from '@/components/beranda/Beranda.vue';
  import Service from '@/components/beranda/Service.vue';
  import { Get } from '@/api/index.js';
  
  export default {
    components: {
      Beranda,Service
    },
    data() {
      return {
        DataHome: [],
        DataLayanan: [],
        DataBlog : []
      }
    },
    async created() {
      // const response = await Get('http://localhost:9000/api/home');
      const response = await Get('http://127.0.0.1:9000/api/home');
      this.DataHome = response.data;
  
      const responseLayanan = await Get('http://127.0.0.1:9000/api/services');
      this.DataLayanan = responseLayanan.data.data;

      const responseBlog = await Get('http://127.0.0.1:9000/api/portfolio');
      this.DataBlog = responseBlog.data.data;
    },
  }
  </script>