<script setup lang="ts">
import { ref } from 'vue';

import TopVue from './components/Top.vue';
import MainVue from './components/Main.vue';
import Bottom from './components/Bottom.vue';

const taskList = ref([{ name: '', isDone: false }]);

taskList.value.pop();

const loadFromStorage = () => {
    const arrayString = localStorage.getItem("taskList");
    if (arrayString) {
        taskList.value = JSON.parse(arrayString);
    }
}

loadFromStorage();

window.addEventListener('storage', loadFromStorage);

const deleteTask = (id: number) => {
    taskList.value = taskList.value.filter((item, index) => index !== id);
    saveToStorage();
};

const clearAllTasks = () => {
    taskList.value = [];
    saveToStorage();
};

const AddTask = (name: string) => {
    const isDone = false
    taskList.value.push({ name, isDone });
    saveToStorage();
};

const changeName = (newName: string, id: number) => {
    taskList.value[id].name = newName;
    saveToStorage();
}

const changeStatus = (id: number) => {
    taskList.value[id].isDone = !taskList.value[id].isDone;
    saveToStorage();
}

const saveToStorage = () => {
    localStorage.setItem("taskList", JSON.stringify(taskList.value));
}

</script>

<template>
    <div class="app-container">
        <header class="app-top">
            <TopVue @addNewTask="AddTask" />
        </header>
        <main class="app-main">
            <MainVue :list="taskList" @deleteTask="(id: number) => deleteTask(id)" @change-name="changeName"
                @changeStatus="changeStatus" />
        </main>
        <footer class="app-bottom">
            <Bottom :count="taskList.length" @clearAllTasks="clearAllTasks()"></Bottom>
        </footer>
    </div>
</template>

<style scoped>
.app-container {
    margin-top: 5px;
    min-width: var(--APP-WIDTH);
    min-height: var(--APP-HEIGHT);
    max-width: 600px;
    width: 20vw;
    height: 80vh;
    border-radius: 45px;
    box-shadow: 2px 2px 2px 2px rgba(0, 0, 0, 0.25);
    background-color: var(--BG-COLOR);
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
    gap: 15px;
    padding: 20px;
    margin-bottom: 10px;
}

.app-top {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

.app-bottom {
    display: flex;
    justify-content: space-around;
    align-items: center;
    gap: 10px;
    width: 90%;
}

.app-main {
    display: flex;
    flex-direction: column;
    overflow-y: auto;
    align-items: center;
    gap: 15px;
    min-width: 360px;
    height: 100%;
    min-height: 115px;
}
</style>
