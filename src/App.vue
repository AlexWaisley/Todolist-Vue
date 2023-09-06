<script setup lang="ts">
import { ref } from 'vue';

import TodolistHeader from './components/TodolistHeader.vue';
import TodolistContent from './components/TodolistContent.vue';
import TodolistFooter from './components/TodolistFooter.vue';

import Task from './modules/Task.ts'

const taskList = ref<Task[]>([{ name: "", isDone: false }]);

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
    taskList.value = taskList.value.filter((_, index) => index !== id);
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
    <div class="todolist-container">
        <TodolistHeader @addNewTask="AddTask" />
        <TodolistContent :list="taskList" @deleteTask="(id: number) => deleteTask(id)" @change-name="changeName"
            @changeStatus="changeStatus" />
        <!-- <TodolistFooter class="todolist-footer" :count="taskList.length" @clearAllTasks="clearAllTasks()" /> -->
    </div>
</template>

<style scoped>
.todolist-container {
    background-color: var(--BG-COLOR);
    width: min(90%, 25rem);
    height: min(90%, 30rem);
    padding: 1rem;
    border-radius: 10px;
    display: flex;
    gap: 1rem;
    flex-direction: column;
}
</style>
