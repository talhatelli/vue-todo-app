<script setup>
import { defineEmits } from 'vue';

const emit = defineEmits(['addTodo',])//'ahmet'

const onAddTodo = (e) => {
    emit('addTodo', e.target.value)
    e.target.value = ''
}

// const onAhmetEmit = () => {
//     emit('ahmet', 'VueJS öğreniyor')
// }
</script>

<template>
    <div class="todo">
        <h1>Todo</h1>
        <input type="text" @keydown.enter="onAddTodo" />
        <!-- <button @click="onAhmetEmit">Ahmet Emit'i fırlat</button> -->
        <hr />
    </div>
</template>