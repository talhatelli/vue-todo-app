<script setup>
import { reactive, computed } from 'vue'

const state = reactive({
  item: null,
  items: [],
});

const addTodo = (event) => {
  state.item = null
  state.items.push({
    id: state.items.length + 1,
    name: event,
    completed: false,
    deleted: false
  });
}

const noDone = computed(() => {
  return state.items.filter((item) => !item.completed && !item.deleted)
})

const deleted = computed(() => {
  return state.items.filter((item) => item.deleted)
})

const uncompleted = computed(() => {
  return state.items.filter((item) => item.completed && !item.deleted)
})
</script>

<template>
  <div class="todo">
    <h1>やることリスト</h1>
    <input type="text" placeholder="あなたの名前を入力してください" v-model="state.item" @keydown.enter="addTodo(state.item)" />
    <hr>
  </div>
  <div class="cards">
    <div class="left">
      <p style="font-size:30px">Todo List</p>
      <ul v-if="noDone.length > 0">
        <li v-for="data in noDone" :key="data.id">
          <input v-model="data.completed" type="checkbox" />
          {{ data.name }}
          <button @click="data.deleted = true"> Delete</button>
        </li>
      </ul>
      <p class="emptylist" v-else>Your todo list is empty.</p>
    </div>
    <div class="right">
      <p style="font-size:30px">Completed</p>
      <ul v-if="uncompleted.length > 0">
        <li v-for="data in uncompleted" :key="data.id">
          <input v-model="data.completed" type="checkbox" />
          {{ data.name }}
          <button @click="data.deleted = true"> Delete</button>
        </li>
      </ul>
    </div>
  </div>
  <!-- Componentler -->
  <div class="deleted">
    <h1>Deleted</h1>
    <ul>
      <li v-for="data in deleted" :key="data.id">
        {{ data.name }}
        <button @click="data.deleted = false"> Restore</button>
      </li>
    </ul>
  </div>
</template>


<style scoped>
* {
  margin: 10;
  padding: 2;
  box-sizing: border-box;
}

.todo input {
  background-color: white;
  min-width: 50%;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 4px;
  font-size: 16px;
}

.cards {
  display: flex;
  background-color: aliceblue;
  justify-content: space-around;
  padding: 0%;
  box-shadow: -20px -20px 0px 0px rgba(100, 100, 100, .1);

}

ul {
  list-style: none;
  padding: 1em;
}

li {
  margin-block: 0.5em;
  padding: 1em;
}

.left {

  background-color: white;
  border: 1px solid lightgray;
  padding: 1em 2em;
  min-width: 300px;

}

.right {
  background-color: white;
  border: 1px solid lightgray;
  padding: 1em 2em;
  min-width: 300px;
}

.emptylist {
  background-color: blanchedalmond;
  margin-top: 2.6rem;
  text-align: center;
  letter-spacing: .05em;
  font-style: italic;
  opacity: 0.8;

}
</style>
