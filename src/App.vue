<template>
  <div id="app">
    <h1>Todo App</h1>
    <hr />
    <AddTodo @add-todo="addTodo"/>
    <TodoList
      v-bind:todos="todos"
      @remove-todo="removeTodo"
    />
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue';
import AddTodo from './components/AddTodo.vue';

export default {
  name: 'App',
  data() {
    return {
      todos: [
        {
          id: 1,
          label: 'Learn vue',
          isCompleted: false,
        },
        {
          id: 2,
          label: 'Upload on git daily',
          isCompleted: false,
        },
        {
          id: 3,
          label: 'Progressively improve',
          isCompleted: false,
        },
      ],
    };
  },
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter((t) => t.id !== id);
    },
    addTodo(newTodo) {
      this.todos.push(newTodo);
    },
  },
  components: {
    AddTodo,
    TodoList,
  },
};
</script>

<style lang="scss">
@import '@/scss/_mixins.scss';

body {
  background-color: dimgray;
}
#app {
  margin-top: 60px;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  color: ghostwhite;
  background-color: dimgray;
}

h1 {
  text-align: center;
  text-transform: uppercase;
}

</style>
