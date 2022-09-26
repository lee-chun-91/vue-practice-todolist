<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoInput :todo-item="todoText" @input="updateTodoText" @addTodo="addTodoItem" ></TodoInput>
    <TodoList :propsdata="todoItems" @removeTodo="removeTodoItem"></TodoList>
    <TodoFooter v-on:removeAll="clearAll"></TodoFooter>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import TodoHeader from "@/components/TodoHeader.vue";
import TodoInput from "@/components/TodoInput.vue";
import TodoList from "@/components/TodoList.vue";
import TodoFooter from "@/components/TodoFooter.vue";


// 할 일 등록
const STORAGE_KEY = 'vue-todo-ts-v1'
const storage = {
  save(todoItems: any[]) {
    const parsed = JSON.stringify(todoItems);
    localStorage.setItem(STORAGE_KEY, parsed);
  },
  fetch() {
    const todoItems = localStorage.getItem(STORAGE_KEY) || "[]";
    const result = JSON.parse(todoItems);
    return result;
  }
}


export default Vue.extend({
  components: { TodoHeader, TodoInput, TodoList, TodoFooter },
  data() {
    return {
      todoText: "",
      todoItems: [] as any[]
    }
  },

  methods: {
    updateTodoText(value: string) {
      this.todoText = value;
    },

    addTodoItem() {
      const value = this.todoText;
      this.todoItems.push(value);
      storage.save(this.todoItems);
      // localStorage.setItem(value, value);
      this.initTodoText();
    },

    initTodoText() {
      this.todoText = "";
    },

    removeTodoItem(index: number) {
      console.log(index);
      this.todoItems.splice(index, 1);
      storage.save(this.todoItems);
    },

    clearAll() {
      localStorage.clear();
      this.todoItems = [];
    },

    fetchTodoItems() {
      this.todoItems = storage.fetch();

    }
  },

  created() {
    this.fetchTodoItems();
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
