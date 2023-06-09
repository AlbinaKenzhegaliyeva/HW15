<template>
  <div class="center">
    <form @submit="addToDo">
      <div>
        <label class="label1">Title</label>
        <input v-model="title" type="text" />
      </div>
      <div>
        <label>Description</label>
        <input v-model="description" type="text" />
      </div>
      <br />
      <div class="btn">
        <button @click="submitTask">ADD</button>
      </div>
    </form>
  </div>
</template>

<script>
export default (await import("vue")).defineComponent({
  name: "TaskForm",
  data() {
    return {
      title: "",
      description: "",
    };
  },
  methods: {
    addToDo(event) {
      event.preventDefault();

      const newTaskObject = {
        id: 5,
        title: this.title,
        description: this.description,
        completed: true,
      };

      this.$emit("add-todo-event", newTaskObject);
      this.title = "";
      this.description = "";
    },
  },
});
</script>

<style>
.label1 {
  padding-right: 50px;
}
button {
  width: 80px;
  height: 30px;
  background-color: green;
  border-radius: 15px;
  color: white;
}
</style>