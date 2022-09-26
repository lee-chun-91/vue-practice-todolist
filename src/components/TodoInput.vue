<template>
  <div class="container">
    <div class="inputBox shadow">
      <label for="todo-input">오늘 할 일 : </label>
      <input id="todo-input" type="text" :value="todoItem" @input="handleInput" placeholder="Type what you have to do"/>
      <span class="addButton">
      <font-awesome-icon icon="fa-solid fa-square-plus" @click="addTodo" />
    </span>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';

export default Vue.extend({
  props: {
    todoItem: {
      type: String,
      required: true
    }
  },

  data() {
    return {
      newTodoItem: ""
    }
  },

  methods: {
    handleInput(event: InputEvent) {
      if (!event.target) {
        return;
      }
      const eventTarget = event.target as HTMLInputElement;
      this.$emit("input", eventTarget.value); // !는 non-null assertion type
    },

    addTodo() {
        this.$emit('addTodo');
    },

    clearInput() {
      this.newTodoItem = "";
    }
  }
})

</script>

<style scoped>
.container {
  display: flex;
  justify-content: center;
}

 input:focus {
   outline: none;
 }
 .inputBox {
   width: 50%;
   background: white;
   height: 50px;
   line-height: 50px;
   border-radius: 5px;
 }
 .inputBox input {
   border-style: none;
   font-size: 0.9rem;
 }

 .addButton {
   margin-left: 10px;
   width: 3rem;
 }

</style>
