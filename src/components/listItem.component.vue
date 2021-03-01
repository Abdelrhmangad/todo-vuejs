<template>
  <div class="taskItem">
    <div :class="taskCompleted ? 'lined' : ''" v-if="task.name !== ''">
      <h4>{{ task.name.toUpperCase() }}</h4>
      <p>
        {{ task.desc }}
      </p>
    </div>
    <p id="error" v-if="task.name === ''">YOU SHOULD PROVIDE A TITLE</p>
    <div>
      <button @click="removeTask">
        <b>X</b>
      </button>
      <button @click="completedTask">
        Done
      </button>
    </div>
  </div>
</template>

<script>
// const error = document.getElementById("error");

export default {
  props: {
    task: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      taskCompleted: false,
    };
  },
  methods: {
    removeTask() {
      this.$emit("removeTask", this.task.id);
    },
    completedTask(e) {
      // const task = e.target.parentNode;
      this.taskCompleted = !this.taskCompleted;
      // if (this.taskCompleted) {
      //   task.style.textDecoration = "line-through";
      //   console.log(e.target.parentNode);
      // } else {
      //   task.style.textDecoration = "none";
      // }
    },
  },
  filters: {
    capitalize: function(value) {
      value.style.textTransform = "uppercase";
    },
  },
};
</script>

<style scoped>
.taskItem {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20;
  padding-right: 50px;
  background: #ffb142;
}
.taskItem div {
  padding-left: 40px;
}
h4 {
  margin-bottom: -10px;
}
button {
  outline: none;
  border: none;
  color: white;
  background: rgb(192 0 0);
  padding: 8px;
  font-size: 14px;
  cursor: pointer;
  border: 2px solid white;
}
#error {
  background: red;
  padding: 20px;
  color: white;
  position: absolute;
  bottom: 0px;
  list-style: none;
}
#error ~ button {
  opacity: 0;
}
.lined {
  text-decoration: line-through !important;
  color: #d35400;
}
</style>
