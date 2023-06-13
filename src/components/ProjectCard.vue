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
    </div>
  </div>
</template>

<style></style>