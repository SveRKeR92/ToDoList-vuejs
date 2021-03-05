<template>
  <div class="columns new-todo">
    <div class="column">
      <input
        type="text"
        placeholder="Add a task..."
        class="input"
        v-model="taskName"
        v-on:keyup.enter="newTask(taskName)"
      />
    </div>
    <div class="column">
      <button class="button is-primary" v-on:click="newTask(taskName)">
        Add
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "NewToDo",
  methods: {
    newTask(input) {
      if (input != null && input != "") {
        console.log(input);
        this.$emit("sendTask", input);
      } else {
        alert("le champ est vide");
      }
    },
  },
};
</script>

<style scoped>
.button {
  font-weight: bold;
}

.column {
  flex-basis: auto;
}
</style>