<template>
  <div class="card box" id="card">
    <div class="columns card-header">
      <div class="column">{{ date }}</div>
      <div class="column green">{{ cardTitle }}</div>
      <div class="column">{{tasks.length}} Tâches</div>
    </div>
    <NewToDo @sendTask="addTask"/>
    
    <ToDoList v-bind:tasks="tasks"/>

  </div>
</template>

<script>
import NewToDo from "./NewToDo.vue";
import ToDoList from './ToDoList.vue';

export default {
  name: "ToDoCard",
  data(){
    return{
      tasks:[]
    }
  },
  computed: {
    date: function () {
      let today = new Date();
      let day = today.toLocaleString("default", { weekday: "long" });
      let month = today.toLocaleString("default", { month: "long" });
      return `${day} ${today.getDay()} ${month}`;
    },
  },
  props: {
    cardTitle: String,
  },
  components: {
    NewToDo,
    ToDoList
  },
  methods:{
    addTask(value){
      this.tasks.push(value);
      console.log('tasks stored : ' + this.tasks)
    }
  }
};
</script>

<style scoped>
.card{
  font-weight: bold;
  font-size: 20px;
}

.columns,
.column {
  background-color: white;
  flex-basis: auto;
}

.green {
  color: springgreen;
}
</style>


