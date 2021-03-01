<template>
  <div class="main">
    <inputText :v-model="val" @toParent="handler" />
    <h2>TASKS:</h2>
    <ul>
      <li v-for="task in tasks" :key="task.id">
        <listItem :task="task" @removeTask="removeTaskHandler" />
        <hr />
      </li>
    </ul>
  </div>
</template>

<script>
import listItem from "./listItem.component";
import inputText from "./input.component";
export default {
  components: {
    listItem,
    inputText,
  },
  data() {
    return {
      val: "this is data",
      tasks: [],
    };
  },
  methods: {
    handler(val) {
      this.val = val;
      console.log("parent " + val);
      const task = {
        name: val.name,
        id: Math.random() * 2312,
        desc: val.desc,
      };
      this.tasks.push(task);
    },
    removeTaskHandler(taskId) {
      this.tasks = this.tasks.filter((each) => {
        return each.id !== taskId;
      });
    },
  },
};
</script>

<style>
.main {
  background: #2980b9;
  width: 90%;
  min-height: 300px;
  padding: 10px;
  margin: 50px auto;
}
ul {
  color: black;
  list-style: none;
  padding-left: 0px;
}
</style>
