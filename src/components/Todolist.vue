<template>
  <div class="content">
    To Do List Vue.js
    <div>
      <div>
        <h3 v-if="incomplete">You still have {{ incomplete }} task to do</h3>
        <h3 v-else>There is no more task to finish ! :)</h3>
      </div>
      <input
        class="input"
        type="text"
        placeholder="enter your task here"
        v-model="newTask"
        @keyup.enter="addTask"
      />
    </div>
    <br />
    <a
      v-for="task in tasks"
      :key="task.id"
      class="task"
      :class="{ completed: task.completed }"
    >
      <div class="todos">
        <input type="checkbox" v-model="task.completed" class="toggle" />
        <label>{{ task.title }}</label>
      </div>
    </a>
    <button @click="clearAll">Clear All Task</button>
  </div>
</template>

<style>
.completed {
  color: green;
  font-style: italic;
  width: 80%;
  margin: auto;
}

.content {
  font-size: 2em;
}

.todos {
  text-align: left;
  margin-left: 30%;
}

.toggle {
  margin-right: 1.5em;
  width: 30px;
  height: 30px;
}

.input {
  width: 40%;
  font-size: 1em;
  margin-top: 1.5em;
}
</style>

<script>
export default {
  name: "todoList",
  data() {
    return {
      newTask: "",
      idTask: [],
      incompleted: [],
      tasks: [],
    };
  },

  computed: {
    incomplete() {
      return this.tasks.filter(this.notCompleted).length;
    },
  },

  methods: {
    addTask() {
      if (this.newTask) {
        this.tasks.push({
          id: this.idTask++,
          title: this.newTask,
          completed: false,
        });
        (this.newTask = ""), this.idTask++;
      }
    },

    clearAll() {
      this.tasks = [];
      this.idTask = 0;
    },

    notCompleted(task) {
      return !task.completed;
    },
  },
};
</script>
