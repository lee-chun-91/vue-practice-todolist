<template>
  <div class="container">
    <div class="inputBox shadow">
      <input type="text" v-model="newTodoItem" placeholder="Type what you have to do"/>
      <span class="addButton">
      <font-awesome-icon icon="fa-solid fa-square-plus" v-on:click="addTodo" />
    </span>
    </div>
  </div>

</template>

<script lang="ts">
import Vue from 'vue';

export default Vue.extend({
  data() {
    return {
      newTodoItem: ""
    }
  },

  methods: {
    addTodo() {
      if (this.newTodoItem !== "") {
        let value = this.newTodoItem && this.newTodoItem.trim();
        localStorage.setItem(value, value);
        this.clearInput();
      }
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
