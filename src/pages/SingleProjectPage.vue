<script>
import axios from 'axios';
export default {
  data() {
    return {
      name: "SingleProjectPage",
      baseURL: "http://127.0.0.1:8000",
      project: {}
    }
  },
  mounted() {
    const slug = this.$route.params.slug;
    axios.get(`${this.baseURL}/api/projects/${slug}`).then(
      resp => {
        console.log(resp);
        this.project = resp.data.results;
      })
  },
  methods: {
    goBack() {
      this.$router.go(-1);
    }
  }
}
</script>

<template>
  <div class="container py-4">
    <h2>{{ project.title }}</h2>
    <p>Slug: {{ project.slug }}</p>
    <p>Contenuto: {{ project.content }}</p>

    <a @click.prevent="goBack()" class="btn btn-primary" href="">Home</a>
  </div>
</template>

<style></style>