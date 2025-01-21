<script setup>
    import { ref } from 'vue';

    const name = ref('Viktor E. Degray');
    const status = ref('loading');
    const tasks = ref(['task 1', 'task 2', 'task 3']);

    const toggleStatus = () => {
        status.value = status.value === 'active' ? 'inactive' : 'active';
    };
</script>

<template>
    <h1>Vue playground by {{ name }}</h1>
    <p v-if="status === 'active'">user exists</p>
    <p v-else-if="status === 'loading'">user is loading in</p>
    <p v-else>user does not exist</p>

    <h3>Tasks:</h3>
    <ul>
        <li v-for="task in tasks" :key="task">{{ task }}</li>
    </ul>
    <br />
    <!-- <button v-on:click="toggleStatus">change status</button> -->
    <button @click="toggleStatus">change status</button>
</template>

<style scoped></style>
