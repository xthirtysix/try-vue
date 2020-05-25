<template>
  <li
    v-bind:class="{'completed': todo.isCompleted, 'move-left': todo.animated}">
    <input type="checkbox" name="todo" :id="todo.id" @change="todo.isCompleted=!todo.isCompleted">
    <label :for="todo.id">{{todo.label}}</label>
    <button @click="todo.animated = !todo.animated, $emit('remove-todo', todo.id)">&times;</button>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      requires: true,
    },
  },
};
</script>

<style lang="scss" scoped>
  @import '@/scss/_mixins.scss';

  li {
    @include shadow;
    display: flex;
    margin: 0.5rem 0;
    padding: 0.5rem 1rem;
    align-items: center;
    background-color: lightslategray;
    border-radius: 1px;

    &:nth-child(even) {
      background-color: slategray;
    }

    &:hover,
    &:active {
      --hover-offset: -5px;
      margin: 0.7rem 0;
      margin-left: var(--hover-offset);
      padding-left: calc(1rem - var(--hover-offset));
    }
  }

  input[type="checkbox"] {
    display: none;
  }

  label {
    margin-right: auto;
    font-family: Avenir, Helvetica, Arial, sans-serif;
    color: ghostwhite;
    cursor: pointer;
  }

  button {
    @include shadow;
    width: 1.5rem;
    height: 1.5rem;
    display: block;
    margin: 0;
    padding: 0;
    font-size: 1.2rem;
    font-weight: 700;
    color: black;
    border: none;
    border-radius: 50%;
    cursor: pointer;
    transition: all 0.3s cubic-bezier(.25,.8,.25,1);
    outline: none;

    li & {
      background-color: slategray;
    }

    li:nth-child(even) & {
      background-color: lightslategray;
    }

    &:hover,
    li:nth-child(even) &:hover {
      color: white;
      background-color: salmon;
    }
  }

  .completed {
    label {
      text-decoration: line-through !important;
    }
  }

  .move-left {
    animation-name: move-left;
    animation-duration: 1s;
  }

  @keyframes move-left {
    100% {
      transform: translateX(-1400px); opacity: 0;
    };
  }
</style>
