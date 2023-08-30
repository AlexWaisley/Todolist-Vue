<script setup lang="ts">
import task from './Task.vue';

const property = defineProps<{
    list: string[],
    removeTask: (id: number) => void
}>();

const deleteTask = (id: number) => {
    property.removeTask(id);
};

const changeTaskName = (newName: string, index: number) => {
    property.list[index] = newName;
};


</script>

<template>
    <task class="task" v-for="(item, index) in property.list" :id="index" :lable="item"
        :onTaskNameChange="(newName: string) => changeTaskName(newName, index)" :onDelete="() => deleteTask(index)">
    </task>
</template>

<style>
.app-main {
    display: flex;
    flex-direction: column;
    overflow-y: auto;
    align-items: center;
    gap: 15px;
    width: 500px;
}

.task {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color: var(--BG-TASK-COLOR);
    box-shadow: 2px 2px 2px 2px rgba(0, 0, 0, 0.25);
    padding: 5px;
    border-radius: 5px;
    min-height: 100px;
    width: 95%;
}
</style>