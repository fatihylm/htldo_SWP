<template>
  <div id="wrapper">
    <h1>TO-DO-LIST</h1>
    <input
      type="text"
      v-model="newTaskText"
      @keyup.enter="addTask"
      placeholder="Add a task"
    />
    <button @click="loadTasks">Load all Tasks</button>
    <ul>
      <li v-for="task in tasks" :key="task.id">
        {{ task.text }}
        <button @click="removeTask(task.id)">X</button>
      </li>
    </ul>
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
      axios.delete(
        `https://to-do-c5706-default-rtdb.europe-west1.firebasedatabase.app/tasks/${id}.json`
      );
      this.tasks = this.tasks.filter((task) => task.id !== id);
    },
  },
};
</script>

<style>
#wrapper {
  margin-top: 5%;
  border: solid gold;
  border-radius: 500px;
  margin-left: 400px;
  margin-right: 400px;
  background-color: black;
  border-width: 5px;
}

text {
  color: greenyellow;
}
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
  height: 50px;
  width: 150px;
  font: 20px sans-serif;
  color: black;
  background-color: gold;
  margin-bottom: 15px;
}
input::placeholder {
  font: 20px/3 sans-serif;
  text-align: center;
}
input {
  display: block;
  margin-right: auto;
  margin-left: auto;
  height: 40px;
  width: 400px;
  margin-bottom: 15px;
}

input[type="text"] {
  font-size: 24px;
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
