<template>
  <div>
    <h3>ToDo List</h3>
    
    <h5 v-if="itemsRemaining > 1 ">There are {{ itemsRemaining}} items left to do today</h5>
    <h5 v-else-if="itemsRemaining < 2 && itemsRemaining === 1">There is {{ itemsRemaining}} item left to do today</h5>
    <h5 v-else-if="itemsRemaining === 0 ">No More items left to do today!!!</h5>
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
      const filteredItems =  this.todos.filter((t) => !t.complete).length;
      console.log(filteredItems)
    return filteredItems
    
    },
  },
};
</script>

<style>

</style>
