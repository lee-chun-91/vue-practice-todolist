<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoInput :todo-item="todoText" @input="updateTodoText" @addTodo="addTodo" ></TodoInput>
    <TodoList :propsdata="todoItems" v-on:removeTodo="removeTodo"></TodoList>
    <TodoFooter v-on:removeAll="clearAll"></TodoFooter>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import TodoHeader from "@/components/TodoHeader.vue";
import TodoInput from "@/components/TodoInput.vue";
import TodoList from "@/components/TodoList.vue";
import TodoFooter from "@/components/TodoFooter.vue";


export default Vue.extend({
  components: { TodoHeader, TodoInput, TodoList, TodoFooter },
  data() {
    return {
      todoText: "",
      todoItems: []
    }
  },

  methods: {
    updateTodoText(value: string) {
      this.todoText = value;
    },

    addTodo() {

      const value = this.todoText

      localStorage.setItem(value, value);
      // this.todoItems.push(value);
      this.initTodoText();
    },

    initTodoText() {
      this.todoText = "";
    },

    removeTodo(todoItem, index) {
      localStorage.removeItem(todoItem);
      this.todoItems.splice(index, 1);
    },

    clearAll() {
      localStorage.clear();
      this.todoItems = [];
    },
  },

  created() {
    if (localStorage.length > 0) {
      for (var i = 0; i < localStorage.length; i++) {
        this.todoItems.push(localStorage.key(i));

      }
    }
  },



})

</script>

<style>
#app {
  display: flex;
  flex-direction: column;
  justify-content: center;

}

body {
  text-align: center;
  background-color: azure;
}

input {
  border-style: groove;
  width: 200px;
}

button {
  border-style: groove;
}
</style>
