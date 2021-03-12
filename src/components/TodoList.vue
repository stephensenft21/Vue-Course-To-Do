<template>
  <div>
    <h3>ToDo List</h3>
    <h5>There are {{ itemsRemaining}} items left to do today</h5>
    <div v-for="item in todos" :key="item.id">
      <todo-item :todo="item" @status-change="handleStatusChange" />
    </div>
  </div>
</template>

<script>
import { todoItems } from "../data";
import TodoItem from "./TodoItem";
export default {
  components: { TodoItem },
  data() {
    return {
      todos: [...todoItems],
    };
  },
  methods: {
    handleStatusChange(item) {
      item.complete = !item.complete;
      console.log(item);
    },
  },

  computed: {
    itemsRemaining() {
      return this.todos.filter((t) => !t.complete).length;
    },
  },
};
</script>

<style>

</style>
