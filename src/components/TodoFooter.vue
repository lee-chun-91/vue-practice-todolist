<template>
  <div class="clearAllContainer">
    <span class="clearAllButton" v-on:click="clearTodo">Clear All</span>
  </div>
</template>

<script>
import Vue from 'vue'

export default Vue.extend({
  methods: {
    clearTodo() {
      this.$emit('removeAll');
    }
  }
})

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
