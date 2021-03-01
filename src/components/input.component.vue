<template>
  <div class="inputs">
    <h1>Add New Tasks</h1>
    <input autofocus type="text" placeholder="Task Title" v-model="task.name" />
    <input type="text" placeholder="Task Body" v-model="task.desc" />
    <button @click="sendNewTask">Add Task</button>
  </div>
</template>

<script>
export default {
  props: ["val"],
  data() {
    return {
      task: {
        name: "",
        desc: "",
      },
    };
  },
  methods: {
    sendNewTask() {
      // if (this.task.name !== "") {
      this.$emit("toParent", this.task);
      this.task = { name: "", desc: "" };
      // }
    },
  },
};
</script>

<style>
.inputs {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 20px;
  background-color: #7d5fff;
  color: white;
}

.inputs input {
  font-size: 1.1em;
  padding: 10px;
  margin: 10px;
  outline: none;
  border: 2px solid #4c745e;
  border-radius: 5px;
}
</style>
