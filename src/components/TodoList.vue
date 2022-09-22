<template>
  <section>
    <ul>
      <li v-bind:key="todoItem" v-for="(todoItem, index) in todoItems">
        <input type="checkbox" />
        {{ todoItem }}
        <button v-on:click="removeTodo(todoItem, index)"> 삭제 </button>
      </li>

    </ul>
  </section>
</template>

<script>
import { Component, Vue } from 'vue-property-decorator'

@Component
export default class TodoList extends Vue {
  todoItems = [];

  created() {
    if (localStorage.length > 0) {
      for (var i = 0; i < localStorage.length; i++) {
        this.todoItems.push(localStorage.key(i));

      }
    }
  }

  removeTodo(todoItem, index) {
    localStorage.removeItem(todoItem);
    this.todoItems.splice(index, 1);
  }
}
</script>

<style scoped>
ul {
  list-style-type: none;
  text-align: left;
}

li {
  display: flex;
  min-height: 50px;
  height: 50px;
  line-height: 50px;
}

</style>
