<template>
  <div>
    <label for="todo-input">오늘 할 일 : </label>
    <input
      id="todo-input"
      type="text"
      :value="item"
      @input="handleInput"
      @keyup.enter="addTodo"
    />
    <button @click="addTodo" type="button">추가</button>
  </div>
</template>

<script lang="ts">
/* eslint-disable */
import Vue from "vue";

export default Vue.extend({
  props: {
    item: {
      type: String,
      default: "",
      required: true,
    },
  },
  methods: {
    handleInput(event: InputEvent) {
      // console.log(event);
      // if(!event.target) return ;
      const eventTarget = event.target as HTMLInputElement;
      this.$emit("input", eventTarget.value);
    },
    addTodo() {
      this.$emit("add");
    },
  },
});
</script>

<style scoped></style>
