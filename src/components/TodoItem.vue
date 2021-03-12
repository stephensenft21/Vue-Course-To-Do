<template>
  <div class="container">
    <v-card class="card" elevation="2" outlined shaped>
      <v-card-title
        >{{ todo.name }}
        <div class="text-center">
          <v-chip
            class="ma-2"
            color="teal"
            @click="handleClick"
            text-color="white"
            v-if="todo.complete"
          >
            <v-avatar left>
              <v-icon >mdi-checkbox-marked-circle</v-icon>
            </v-avatar>
          </v-chip>
        </div>
      </v-card-title>
      <v-row justify="space-around">
        <v-card-actions @click="handleClick"
          ><v-btn class="completed-button" x-large elevation="2">{{
            buttonText
          }}</v-btn></v-card-actions
        >
      </v-row>
    </v-card>
  </div>
</template>

<script>
export default {
  props: ["todo"],
  methods: {
    handleClick() {
      this.$emit("status-change", this.todo);
      console.log("completed button clicked");
    },
  },
  computed: {
    buttonText() {
      return this.todo.complete ? "Mark Incomplete" : "Mark Complete";
    },
  },
};
</script>

<style scoped>
.card {
  width: 500px;
  height: 155px;
  margin: 15px;
  padding: 10px;
}
.completed-button {
  margin: 15px;
  padding: 15px;
}
.container {
  margin-left: 50px;
  margin-right: 50px;
  padding: 10px;
}
</style>
