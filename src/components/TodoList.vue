<template>
  <section>
    <transition-group name="list" tag="ul">
<!--      v-for 을 사용하는 경우 :key 값 더해주어야. 일단은 v-for 에서 제공하는 index 할당-->
      <li :key="index" v-for="(todoItem, index) in propsdata" >
<!--        <span class="checkBox">-->
<!--           <input type="checkbox" />-->
<!--        </span>-->
        <span class="item complete" @click="toggleItem(todoItem, index)">
           {{ todoItem }}
        </span>
        <span class="deleteButton">
          <font-awesome-icon @click="removeTodo(todoItem, index)" icon="fa-solid fa-trash" />
        </span>
      </li>
    </transition-group>
  </section>
</template>

<script lang="ts">
import Vue, {PropType} from 'vue'
import {Todo} from "@/App.vue";

export default Vue.extend({
  props: {
    propsdata: {
      type: [] as PropType<Todo[]>,
    }
  },

  methods: {
    toggleItem() {
      this.$emit("toggle", )
    },
    removeTodo(index: number) {
      this.$emit('removeTodo', index);
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

  input {
    width: 20px;
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

  .item {
    cursor: pointer;
  }

  .complete {
    text-decoration: line-through;
  }

  .deleteButton {
    margin-left: 20px;
  }

</style>
