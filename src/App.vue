<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoInput></TodoInput>
    <TodoList></TodoList>
    <TodoFooter></TodoFooter>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'
import TodoHeader from "@/components/TodoHeader.vue";
import TodoInput from "@/components/TodoInput.vue";
import TodoList from "@/components/TodoList.vue";
import TodoFooter from "@/components/TodoFooter.vue";


@Component({
  components: { TodoHeader, TodoInput, TodoList, TodoFooter },
})
export default class App extends Vue {
  data() {
    return {
      // todolist 의 type 설정 및 적용 필요
      listdata: [],
    };
  }
  // addtodo 메서드 등록 필요
}
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
