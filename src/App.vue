<script setup>
import { reactive } from 'vue'
const state = reactive({
  item: null,
  items: [
    {
      id: 1,
      name: "ahmet",
      completed: false,
      deleted: false
    },],
});

const addTodo = (event) => {
  state.liste = null,

    state.items.push({
      id: new Date().getTime(),
      name: event,
      completed: false,
      deleted: false
    });
}
const noDone = (() => {
  return todos.filter((item) => !item.completed)
})
const completed = (() => {
  return todos.filter((items) => items.completed)
})
</script>

<template>
  <div>
    <h1>Todo List</h1>
    <input type="text" placeholder="あなたの名前を入力してください" v-model="state.liste" @keydown.enter="addTodo(state.liste)" />
    <ul>
      <li v-for="data in state.items" :key="data.id">
        <div v-if="noDone">
          <div v-if="!data.deleted">
            <input v-model="data.completed" type="checkbox" />
            {{ data.name }}
            <button @click="data.deleted = true"> Sil</button>
          </div>
        </div>
      </li>
    </ul>
    <br />
    <ul>
      <li v-for="data in state.items" :key="data.id">
        <div v-if="completed">
          <div v-if="!data.deleted">
            <input v-model="data.completed" type="checkbox" />
            {{ data.name }}
            <button @click="data.deleted = true"> Sil</button>
          </div>
        </div>
      </li>
    </ul>
  </div>
</template>

<style scoped>
ul {
  list-style: none;
}
</style>
