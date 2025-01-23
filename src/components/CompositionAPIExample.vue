<script setup>
import { ref, onMounted } from 'vue';

const name = ref('Viktor E. Degray');
const status = ref('loading');
const tasks = ref(['task 1', 'task 2', 'task 3']);
const newTask = ref('');

const toggleStatus = () => {
    status.value = status.value === 'active' ? 'inactive' : 'active';
};

const addTask = () => {
    if (!newTask.value) return;
    tasks.value.push(newTask.value.trim());
    newTask.value = '';
};

const deleteTask = (index) => {
    tasks.value.splice(index, 1);
};

onMounted(async () => {
    try {
        const response = await fetch('https://jsonplaceholder.typicode.com/todos');
        const data = await response.json();
        tasks.value = data.map((task) => task.title);
    } catch (error) {
        console.log('error fetching tasks:', error);
        
    }
});
</script>

<template>
    <h1>Vue playground by {{ name }}</h1>
    <p v-if="status === 'active'">user exists</p>
    <p v-else-if="status === 'loading'">user is loading in</p>
    <p v-else>user does not exist</p>
    <br />

    <form @submit.prevent="addTask">
        <label for="newTask">Add task:</label>
        <br />
        <input type="text" id="newTask" name="newTask" v-model="newTask" />
        <button type="submit">add task</button>
    </form>
    <br />

    <h3>Tasks:</h3>
    <ul>
        <li v-for="(task, index) in tasks" :key="task">
            <span>{{ task }}</span>
            <button @click="deleteTask(index)">X</button>
        </li>
    </ul>
    <br />
    <!-- <button v-on:click="toggleStatus">change status</button> -->
    <button @click="toggleStatus">change status</button>
</template>

<style scoped></style>
