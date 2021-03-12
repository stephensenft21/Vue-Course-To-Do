<template>
  <div >
    <v-banner>ToDo List
    <h5 v-if="itemsRemaining > 1 ">There are {{ itemsRemaining}} items left to do today</h5>
    <h5 v-else-if="itemsRemaining < 2 && itemsRemaining === 1">There is {{ itemsRemaining}} item left to complete today</h5>
    <h5 v-else-if="itemsRemaining === 0 ">No More items left to do today!!!</h5>
    </v-banner>
    <v-card class="todo-items">
    <div  v-for="item in todos" :key="item.id">
      <todo-item  :todo="item" @status-change="handleStatusChange" />
    </div>
    </v-card>
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


.todo-items {
  display: flex;
align-items: center;
flex-direction: column;
margin-left: 100px;
margin-right: 100px;
padding-left: 20px;
padding-right: 20px;


}
</style>
