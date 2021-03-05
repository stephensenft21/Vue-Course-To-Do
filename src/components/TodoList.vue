<template>
  <div>
    <h3>ToDo List</h3>
    <div v-for="item in todos" :key="item.id">
      <todo-item :todo="item" @status-change="handleStatusChange" />
    </div>
  </div>
</template>

<script>
import { todoItems } from "";
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
};
</script>

<style></style>
