<template>
  <section>
    <transition-group name="list" tag="ul">
      <li :key="todoItem" v-for="(todoItem, index) in propsdata" >
        <span class="checkBox">
           <input type="checkbox" />
        </span>
        {{ todoItem }}
        <span class="deleteButton">
          <font-awesome-icon v-on:click="removeTodo(todoItem, index)" icon="fa-solid fa-trash" />
        </span>
      </li>
    </transition-group>
  </section>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  props: ['propsdata'],

  methods: {
    removeTodo(todoItem:string, index: number) {
      this.$emit('removeTodo', todoItem, index);
    }
  }


})
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
