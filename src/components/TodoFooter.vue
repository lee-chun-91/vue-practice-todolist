<template>
  <div class="clearAllContainer">
    <span class="clearAllButton" v-on:click="clearAllTodo">Clear All</span>
  </div>
</template>

<script>
import { Component, Vue } from 'vue-property-decorator';

@Component
export default class TodoFooter extends Vue {
  clearAllTodo() {
    localStorage.clear();
  }
}

</script>

<style scoped>
  .clearAllContainer {
    width: 8rem;
    height: 50px;
    line-height: 50px;
    background-color: white;
    border-radius: 5px;
    margin: 0 auto;
  }

  .clearAllButton {
    color: blue;
    display: block;
  }

</style>
