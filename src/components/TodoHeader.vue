<template>
  <header>
    <h1>To Do List </h1>
  </header>
</template>

<script>
import { Component, Vue } from 'vue-property-decorator'

@Component
export default class TodoHeader extends Vue {}

</script>

<style scoped>
h1 {
  color: blue;
  font-weight: 600;
  margin: 2.5rem 0 1.5rem;
}

</style>
