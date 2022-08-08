<script setup>
const props = defineProps({
    middleman: Array,
});
</script>
<template>
    <div class="right">
        <p style="font-size:30px">Completed</p>
        <ul v-if="props.middleman.length > 0">
            <li v-for="data in props.middleman" :key="data.id">
                <input v-model="data.completed" type="checkbox" />
                {{ data.name }}
                <button @click="data.deleted = true"> Delete</button>
            </li>
        </ul>
        <p class="emptylist" v-else>come on bro, throw me what's been done.</p>
    </div>
</template>