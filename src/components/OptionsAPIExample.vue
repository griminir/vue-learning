<!-- use of options api -->
<script>
export default {
    data() {
        return {
            name: 'Viktor E. Degray',
            status: 'loading',
            tasks: ['task 1', 'task 2', 'task 3'],
            link: 'https://vuejs.org',
        };
    },
    methods: {
        toggleStatus() {
            this.status = this.status === 'active' ? 'inactive' : 'active';
        },
    },
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
    <!-- <a v-bind:href="link" target="_blank">documentation</a> -->
    <a :href="link" target="_blank">click for vue documentation</a>
    <br />
    <!-- <button v-on:click="toggleStatus">change status</button> -->
    <button @click="toggleStatus">change status</button>
</template>
