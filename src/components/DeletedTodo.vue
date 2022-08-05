<script setup>
const props = defineProps({
  items: Array,
});

</script>

<template>

  <div class="deleted">
    {{ props.deleted }}
    <h1>Deleted</h1>
    <ul>
      <li v-for="data in props.items" :key="data.id">
        {{ data.name }}
        <button @click="data.deleted = false"> Restore</button>
      </li>
    </ul>
  </div>
</template>

<style scoped>
</style>