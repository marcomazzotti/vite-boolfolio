<script>
import axios from 'axios';
import ProjectCard from '../components/ProjectCard.vue';

export default {
  data() {
    return {
      baseURL: "http://127.0.0.1:8000",
      projects: [],
      currentPage: 1,
      lastPage: null,
      totalProjects: 0
    };
  },
  mounted() {
    this.getProjects();
  },
  methods: {
    getProjects(pageNumber = 1) {
      axios.get(`${this.baseURL}/api/projects`, {
        params: {
          page: pageNumber
        }
      }).then(resp => {
        // console.log(resp);
        this.projects = resp.data.results.data;
        this.currentPage = resp.data.results.current_page;
        this.lastPage = resp.data.results.last_page;
        this.totalProjects = resp.data.results.total;
      });
    }
  },
  components: { ProjectCard }
}
</script>

<template>
  <div class="container">
    <h1 class="text-center my-4">Tutti i progetti</h1>
    <div class="text-end">
      <h6>trovati {{ totalProjects }} progetti</h6>
    </div>
    <div class="row row-cols-4 g-4">
      <div class="col" v-for="project in projects" :key="project.id">
        <ProjectCard :project="project" />
      </div>
    </div>
    <nav v-if="lastPage" class="mt-4 d-flex justify-content-center" aria-label="Page navigation example">
      <ul class="pagination">
        <li class="page-item" :class="{ 'disabled': currentPage === 1 }"><a @click.prevent="getProjects(currentPage - 1)"
            class="page-link" href="#">Previous</a></li>
        <li class="page-item" :class="{ 'active': pageNum === currentPage }" v-for="pageNum in lastPage">
          <a @click.prevent="getProjects(pageNum)" class="page-link" href="#">{{ pageNum }}</a>
        </li>
        <li class="page-item" :class="{ 'disabled': currentPage === lastPage }"><a
            @click.prevent="getProjects(currentPage + 1)" class="page-link" href="#">Next</a></li>
      </ul>
    </nav>
  </div>
</template>