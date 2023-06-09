<template>
  <br />
  <div>
    <h2>You got {{ countTasks }} tasks</h2>
    <h2>You got {{ countCompletedTasks }} completed tasks</h2>
  </div>
  <ul>
    <li>
      <Task
        v-bind:task="task"
        v-for="(task, index) in tasks"
        :key="task.id"
        @remove="removeTask(index)"
        :class="['input', { done: task.completed === true }]"
      />
    </li>
  </ul>
</template> 

<script>
import Task from "./Task.vue";

export default (await import("vue")).defineComponent({
  name: "TaskList",
  props: ["tasks"],
  components: { Task },
  computed: {
    countTasks() {
      return this.tasks.length;
    },
    countCompletedTasks() {
      return this.tasks.filter(this.inProgress).length;
    },
  },
  methods: {
    removeTask(index) {
      this.tasks.splice(index, 1);
    },
    inProgress(task) {
      return this.isCompleted(task);
    },
    isCompleted(task) {
      return task.completed;
    },
  },
});
</script>  

<style>
li {
  list-style-type: none;
}
.done {
  color: blue;
}
</style>