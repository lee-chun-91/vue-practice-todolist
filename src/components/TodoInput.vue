<template>
  <div>
    <input type="text" v-model="newTodoItem" />
    <button v-on:click="addTodo">추가</button>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";

@Component
export default class TodoInput extends Vue {
  newTodoItem = "";

  addTodo() {
    if (this.newTodoItem !== "") {
      var value = this.newTodoItem && this.newTodoItem.trim();
      localStorage.setItem(value, value);
      this.clearInput();
    }
  }
  clearInput() {
    this.newTodoItem = "";
  }
}
</script>

<style scoped></style>
