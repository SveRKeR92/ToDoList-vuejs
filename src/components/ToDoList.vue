<template>
  <div class="columns to-do-list" v-for="(task, index) in tasks" v-bind:key="task">
    <div class="column">
      <input type="checkbox" class="checkbox" :data-index="index"/>
    </div>
    <div class="column taskTitle" :data-index="index">
      <p> {{index + 1}} - {{ task }} </p>
    </div>
    <div class="column">
      <button class="button is-danger" :data-index="index">Delete</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "ToDoList",
  props:{
    tasks: Array
  }
};
</script>

<style scoped>
.column{
  flex-basis: auto;
}
</style>