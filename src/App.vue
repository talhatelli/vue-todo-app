<script setup>
import { reactive, computed } from 'vue'
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
  state.item = null
  state.items.push({
    id: state.items.length + 1,
    name: event,
    completed: false,
    deleted: false
  });

}


const noDone = computed(() => {
  return state.items.filter((item) => !item.completed)
})



const uncompleted = computed(() => {
  return state.items.filter((item) => item.completed)
})

</script>






<template>
  <div class="todo">
    <h1>やることリスト</h1>
    <input type="text" placeholder="あなたの名前を入力してください" v-model="state.item" @keydown.enter="addTodo(state.item)" />
    <hr>
    <ul v-if="noDone.length > 0">
      <li v-for="data in noDone" :key="data.id">
        <div v-if="!data.deleted">
          <input v-model="data.completed" type="checkbox" />
          {{ data.name }}
          <button @click="data.deleted = true"> Sil</button>
        </div>
      </li>
    </ul>
    <br />
    <ul v-if="uncompleted.length > 0">
      <li v-for="data in uncompleted" :key="data.id">
        <div v-if="!data.deleted">
          <input v-model="data.completed" type="checkbox" />
          {{ data.name }}
          <button @click="data.deleted = true"> Sil</button>
        </div>
      </li>
    </ul>
  </div>
</template>

<style scoped>
.todo input {

  background-color: white;
  min-width: 50%;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 4px;
  font-size: 16px;
}
</style>
