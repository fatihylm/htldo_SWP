<template>
  <todo-list></todo-list>
</template>

<script>
import TodoList from './components/todoList.vue';

export default {
  name: "App",
  components: {
    TodoList,
  },
};
</script>