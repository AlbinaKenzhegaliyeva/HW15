<template>
  <div class="task">
    <ul>
      <li>{{ task.title }}</li>
      <li>{{ task.description }}</li>
      <li>
        <input type="checkbox" @click="check" v-model="task.completed" />
        {{ task.completed }}
      </li>
    </ul>
    <button @click="$emit('remove')" class="delete">DELETE</button>
  </div>
</template> 

<script>
export default (await import("vue")).defineComponent({
  name: "Task",
  props: ["task"],
  methods: {
    check(task) {
      task.checked = true;
    },
  },
});
</script>  

<style>
li {
  list-style-type: none;
}
.delete {
  background-color: red;
  margin-left: 50px;
}
.task {
  padding-bottom: 20px;
  margin-left: 0;
}
</style>