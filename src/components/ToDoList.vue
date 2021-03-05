<template>
  <div class="columns to-do-list" v-for="(task, index) in tasks" v-bind:key="task" >
    <div class="column">
      <input type="checkbox" class="checkbox" :data-index="index" v-on:click="check(index), changeStatus($event)" />
    </div>
    <div class="column taskTitle" :data-index="index" v-bind:class="{'checked': isChecked }" >
      <p>{{ task.name }}</p>
    </div>
    <div class="column">
      <button class="button is-danger" :data-index="index" v-on:click="remove(index)" > Delete </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "ToDoList",
  data() {
    return {
      isChecked: false,
    };
  },
  props: {
    tasks: Array,
  },
  methods: {
    check(index) {
      this.$emit("check", index);
    },
    remove(index){
      this.$emit("remove", index);
    },

    changeStatus(event) { //j'arrive pas avec le emit
      let selected = event.currentTarget;
      let index = selected.getAttribute("data-index");
      let tasks = document.getElementsByClassName("taskTitle");
      console.log(tasks[index]);
      tasks[index].classList.toggle("checked"); // à l'ancienne avec javascript
    },
  },
};
</script>

<style scoped>
.column {
  flex-basis: auto;
}

.checked {
  text-decoration: line-through;
}
</style>