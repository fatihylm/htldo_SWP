<template>
  <div>
    <ul>
      <li v-for="task in tasks" :key="task.id">{{ task.text }} <button @click="removeTask(task.id)">X</button></li>
    </ul>
    <input v-model="newTaskText" @keyup.enter="addTask" placeholder="Add a task">
  </div>
</template>

<script>
export default {
  data() {
    return {
      tasks: [],
      newTaskText: ''
    }
  },
  methods: {
    addTask() {
      this.tasks.push({
        id: Date.now(),
        text: this.newTaskText
      })
      this.newTaskText = ''
    },
    removeTask(id) {
      this.tasks = this.tasks.filter(task => task.id !== id)
    }
  }
}
</script>
