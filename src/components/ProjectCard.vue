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
      </p>
    </div>
  </div>
</template>

<style></style>