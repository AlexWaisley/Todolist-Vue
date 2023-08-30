<script setup lang="ts">
import { ref } from 'vue';

import TopVue from './components/Top.vue';
import MainVue from './components/Main.vue';
import Bottom from './components/Bottom.vue';


const taskList = ref(["New task"]);

taskList.value.push("New task1");
taskList.value.push("New task2");
taskList.value.push("New task3");
taskList.value.push("New task4");

const deleteTask = (id: number) => {
    taskList.value = taskList.value.filter((item, index) => index !== id);
};

const clearAllTasks = () => {
    taskList.value = [];
};

const AddTask = (name: string) => {
    taskList.value.push(name);
};

</script>

<template>
    <div class="app-container">
        <header class="app-top">
            <TopVue :addTask="(newName: string) => AddTask(newName)" />
        </header>
        <main class="app-main">
            <MainVue :list="taskList" :remove-task="(id: number) => deleteTask(id)" />
        </main>
        <footer class="app-bottom">
            <Bottom :count="taskList.length" :clear-all-task="clearAllTasks"></Bottom>
        </footer>
    </div>
</template>

<style scoped>
.app-container {
    width: 600px;
    height: 850px;
    border-radius: 45px;
    box-shadow: 2px 2px 2px 2px rgba(0, 0, 0, 0.25);
    background-color: var(--BG-COLOR);
    display: grid;
    grid-template-rows: 25% 55% 20%;
    place-content: center;
}

.app-top {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

.app-top-name {
    font-size: var(--FS-XL);
}

.app-top-add-task-container {
    display: flex;
    gap: 10px;
    justify-content: center;
    align-items: center;
}

.add-btn {
    width: 100px;
    height: 100px;
    display: grid;
    border-radius: 5px;
    place-content: center;
    background-color: var(--BTN-BG-COLOR);
    box-shadow: 2px 2px 2px 2px rgba(0, 0, 0, 0.25);
}

.add-btn:hover {
    cursor: pointer;
    background-color: var(--BTN-BG-COLOR-HOVER);
}

.add-task-name {
    height: 100px;
    width: 320px;
    font-size: var(--FS-XL);
    border-radius: 5px;
    box-shadow: 2px 2px 2px 2px rgba(0, 0, 0, 0.25);
    padding: 0 10px 0 10px;
}

.app-bottom {
    display: flex;
    justify-content: space-around;
    align-items: center;
}

.app-main {
    display: flex;
    flex-direction: column;
    overflow-y: auto;
    align-items: center;
    gap: 15px;
    width: 500px;
}
</style>
