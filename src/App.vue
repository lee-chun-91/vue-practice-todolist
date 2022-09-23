<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoInput v-on:addTodo="addTodo"></TodoInput>
    <TodoList :parent-message="test1"></TodoList>
    <TodoFooter></TodoFooter>
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
      test1: "안녕",
      todoItems: []
    }
  },

  methods: {
    addTodo() {
      console.log("click addTodo");
    }
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
