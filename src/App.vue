<template>
  <h1>Home work 15</h1>
  <TaskList v-bind:tasks="tasks" />
  <TaskForm @add-todo-event="addToDoItem" />
</template>

<script>
import TaskList from "./components/TaskList.vue";
import TaskForm from "./components/TaskForm.vue";

export default {
  components: {
    TaskList,
    TaskForm,
  },
  data() {
    return {
      activeColor: "green",
      tasks: [
        {
          id: 0,
          title: "Eat",
          description: "Eat some food for breakfast",
          completed: true,
        },
        {
          id: 1,
          title: "Sleep",
          description: "Sleep 8 hours",
          completed: true,
        },
        {
          id: 2,
          title: "Code",
          description: "Do your homework",
          completed: true,
        },
        {
          id: 3,
          title: "Sport",
          description: "Running, gym and etc.",
          completed: false,
        },
        {
          id: 4,
          title: "Work",
          description: "Work work work",
          completed: false,
        },
      ],
    };
  },
  methods: {
    addToDoItem(newTask) {
      this.tasks = [...this.tasks, newTask];
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
