<template>
  <form class="wrapper">
    <div class="input-container">
      <input type="text" placeholder="What needs to be done?">
      <label class="label">What needs to be done?</label>
    </div>
    <button type="submit">Create</button>
  </form>
</template>

<style lang="scss" scoped>
@import '@/scss/_mixins.scss';

.wrapper {
  padding: 0 1rem;
  display: flex;
}

.input-container {
  position: relative;
  min-width: 250px;
  height: 100%;
}

input[type="text"] {
  box-sizing: border-box;
  position: relative;
  z-index: 2;
  top: 0;
  left: 0;
  display: block;
  width: 100%;
  padding: 1rem 0 1rem 0.5rem;
  color: ghostwhite;
  background-color: transparent;
  border: 2px solid transparent;
  border-bottom: 2px solid lightslategray;
  outline: none;
  transition: 0.4 ease-in;

  &:focus,
  &:not(:placeholder-shown) {
    + label {
      z-index: 10;
      top: 2%;
      display: block;
      padding: 0 5px;
      font-size: 0.7rem;
      color: ghostwhite;
      background-color: dimgray;
    }
  }

  &:focus {
    border: 2px solid slategray;
  }

  &::placeholder {
    color: transparent;
  }
}

label {
  position: absolute;
  z-index: 1;
  top: 50%;
  left: 0.5rem;
  transform: translateY(-50%);
  color: ghostwhite;
  transition: 0.15s ease-in;
}

button {
  @include shadow;
  padding: 0.5rem 1rem;
  color: ghostwhite;
  background-color: lightslategrey;
  border: 2px solid lightslategrey;
  outline: none;
}
</style>
