<template>
  <ul>
    <TodoItem
      v-for="(todo, i) in todos"
      :key="todo.id"
      :todo="todo"
      :index="i"
      @:remove-todo="removeTodo"/>
  </ul>
</template>

<script>
import TodoItem from './TodoItem.vue';

export default {
  props: ['todos'],
  methods: {
    removeTodo(id) {
      this.$emit('remove-todo', id);
    },
  },
  components: {
    TodoItem,
  },
};
</script>

<style lang="scss" scoped>
ul {
  margin: 0;
  padding: 1rem;
  list-style: none;
}
</style>
