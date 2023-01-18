<template>
  <div>
    <h1>TO-DO-LIST</h1>
    <button @click="loadTasks">Load all Tasks</button>
    <ul>
      <li v-for="task in tasks" :key="task.id">
        {{ task.text }}
        <button @click="removeTask(task.id)">X</button>
      </li>
    </ul>
    <input
      v-model="newTaskText"
      @keyup.enter="addTask"
      placeholder="Add a task"
    />
  </div>
</template>
<script>
import axios from "axios";
export default {
  data() {
    return {
      tasks: [],
      newTaskText: "",
    };
  },
  methods: {
    addTask() {
      axios
        .post(
          "https://to-do-c5706-default-rtdb.europe-west1.firebasedatabase.app/tasks.json",
          {
            text: this.newTaskText,
          }
        )
        .then((response) => {
          this.tasks.push({
            id: response.data.name,
            text: this.newTaskText,
          });
          this.newTaskText = "";
        })
        .catch((error) => {
          console.log(error);
        });
    },
    loadTasks() {
      axios
        .get(
          "https://to-do-c5706-default-rtdb.europe-west1.firebasedatabase.app/tasks.json"
        )
        .then((response) => {
          this.tasks = Object.values(response.data);
        })
        .catch((error) => {
          console.log(error);
        });
    },
    removeTask(id) {
      this.tasks = this.tasks.filter((task) => task.id !== id);
    },
  },
};
</script>

<style>
h1 {
  text-align: center;
  font-weight: 600;
  font-size: 3rem;
  color: gold;
}
button {
  display: block;
  margin-right: auto;
  margin-left: auto;
}

input {
  display: block;
  margin-right: auto;
  margin-left: auto;
  height: 25px;
  width: 300px;
}
li {
  color: white;
}
ul {
  display: table;
  margin: 0 auto;
  margin-bottom: 15px;
}

body {
  background-color: grey;
}
</style>
