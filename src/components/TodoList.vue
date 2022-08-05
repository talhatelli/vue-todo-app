<script setup>
const props = defineProps({
    shipment: Array,
});
</script>

<template>
    <div class="cards">

        <div class="left">
            <p style="font-size:30px">Todo List</p>
            <ul v-if="props.shipment.length > 0">
                <li v-for="data in props.shipment" :key="data.id">
                    <input v-model="data.completed" type="checkbox" />
                    {{ data.name }}
                    <button @click="data.deleted = true"> Delete</button>
                </li>
            </ul>
            <p class="emptylist" v-else>Your todo list is empty.</p>
        </div>
    </div>
</template>