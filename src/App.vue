<script setup>
import { reactive, computed } from "vue";
import TodoList from "./components/TodoList.vue";
import CompletedTodo from "./components/CompletedTodo.vue";
import TitleTodo from "./components/TitleTodo.vue";
import DeletedTodo from "./components/DeletedTodo.vue";

const state = reactive({
  items: [],
});

const addTodo = (name) => {
  state.items.push({
    id: state.items.length + 1,
    name: name,
    completed: false,
    deleted: false,
  });

};

const noDone = computed(() => {
  return state.items.filter((item) => !item.completed && !item.deleted);
});

const uncompleted = computed(() => {
  return state.items.filter((item) => item.completed && !item.deleted);
});

//console.log("done", noDone);
//console.log("completed", uncompleted);

const deleted = computed(() => {
  return state.items.filter((item) => item.deleted);
});

// const onComeAhmet = (info) => {
//   alert(info)
// }
</script>

<template>
  <TitleTodo @add-todo="addTodo" /> <!-- @ahmet="onComeAhmet" -->
  <div class="cards">
    <TodoList :shipment="noDone" />
    <CompletedTodo :middleman="uncompleted" />
  </div>
  <DeletedTodo :items="deleted" />
</template>

<style scoped>
* {
  margin: 10;
  padding: 2;
  box-sizing: border-box;
}
</style>
