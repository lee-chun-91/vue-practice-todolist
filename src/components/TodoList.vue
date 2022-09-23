<template>
  <section>
    <ul>
      <li v-bind:key="todoItem" v-for="(todoItem, index) in todoItems">
        <span class="checkBox">
           <input type="checkbox" />
        </span>
        {{ todoItem }}
        <span class="deleteButton">
          <font-awesome-icon v-on:click="removeTodo(todoItem, index)" icon="fa-solid fa-trash" />
        </span>

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
  display: flex;
  flex-direction: column;
  align-items: center;
}

li {
  display: flex;
  width: 50%;
  min-height: 50px;
  height: 50px;
  line-height: 50px;
  background: white;
  margin: 0.5rem 0;
  border-radius: 5px;
}

.deleteButton {
  margin-left: 20px;
}

</style>
