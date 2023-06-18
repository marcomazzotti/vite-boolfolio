<script>
export default {
  name: "ProjectCard",
  props: {
    project: Object
  }
}
</script>

<template>
  <div class="card h-100">
    <div class="card-body">
      <h4>{{ project.title }}</h4>
      <p>
        <span v-if="project.type">Tipo di progetto: {{ project.type.name }}</span>
        <span v-else>Nessun tipo specificato</span>
      <div class="my-4">
        <router-link :to="{ name: 'single-project', params: { slug: project.slug } }"
          class="btn btn-primary">Leggi</router-link>
      </div>

      </p>
    </div>
  </div>
</template>

<style></style>