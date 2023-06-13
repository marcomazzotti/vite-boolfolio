import axios from 'axios';

<script>
export default{
  data() {
    return {
      projects: []
    }
  },
  mounted(){
    this.getProjects();
  },
  methods: {
    getProjects() {
      axios.get("http://127.0.0.1:8000/api/projects").then(resp => {
        this.projects = resp.data.results;
        console.log(resp);
      })
    }
  }
}
</script>

<template>
<h1>Tutti i progetti</h1>
</template>

<style lang="scss">
@use "./styles/general.scss"
</style>
