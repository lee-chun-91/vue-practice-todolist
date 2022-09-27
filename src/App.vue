<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoInput :todo-item="todoText" @input="updateTodoText" @addTodo="addTodoItem" ></TodoInput>
    <TodoList :propsdata="todoItems" @toggle="toggleTodoItemComplete" @removeTodo="removeTodoItem"></TodoList>
    <TodoFooter v-on:removeAll="clearAll"></TodoFooter>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import TodoHeader from "@/components/TodoHeader.vue";
import TodoInput from "@/components/TodoInput.vue";
import TodoList from "@/components/TodoList.vue";
import TodoFooter from "@/components/TodoFooter.vue";

export interface Todo {
  title: string;
  done: boolean;
}


// 할 일 등록
const STORAGE_KEY = 'vue-todo-ts-v1'
const storage = {
  save(todoItems: Todo[]) {
    const parsed = JSON.stringify(todoItems);
    localStorage.setItem(STORAGE_KEY, parsed);
  },

  fetch(): Todo[] {
    const todoItems = localStorage.getItem(STORAGE_KEY) || "[]";
    const result = JSON.parse(todoItems);
    return result;
  },
}

export default Vue.extend({
  components: { TodoHeader, TodoInput, TodoList, TodoFooter },
  data() {
    return {
      todoText: "",
      todoItems: [] as Todo[]
    }
  },

  methods: {
    fetchTodoItems() {
      this.todoItems = storage.fetch().sort((a, b) => {
        if (a.title < b.title) {
          return -1;
        }
        if (a.title > b.title) {
          return 1;
        }
        return 0;
      });
    },

    updateTodoText(value: string) {
      this.todoText = value;
    },

    addTodoItem() {
      const value = this.todoText;
      const todo: Todo = {
        title: value,
        done: false
      }
      this.todoItems.push(todo);
      storage.save(this.todoItems);
      // localStorage.setItem(value, value);
      this.initTodoText();
    },

    initTodoText() {
      this.todoText = "";
    },

    toggleTodoItemComplete(todoItem: Todo, index: number) {
      this.todoItems.splice(index, 1, {
        ...todoItem, done: !todoItem.done
      });
      storage.save(this.todoItems);
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
  },

  created() {
    this.fetchTodoItems();
  }
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
