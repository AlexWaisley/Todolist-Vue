<script setup lang="ts">

import { ref } from 'vue';

const property = defineProps<{
    id: number,
    lable: string,
    onTaskNameChange: (name: string) => void,
    onDelete: () => void
}>();

const isDone = ref(false);

const changeStatus = () => {
    isDone.value = !isDone.value;
};

</script>

<template>
    <div class="task">
        <button type="button" class="mark-btn" @click="changeStatus()">
            <div v-if="isDone">
                <img src="../assets/double-check-svgrepo-com.svg" alt="Change status">
            </div>
            <div v-else>
                <img src="../assets/tick-svgrepo-com.svg" alt="Change status">
            </div>
        </button>
        <div class="task-lable" v-bind:class="{ 'line-through': isDone }">{{ property.lable }}</div>
        <button type="button" class="delete-btn" @click="() => { onDelete(); isDone = false; }">
            <img src="../assets/delete.svg" alt="Delete">
        </button>
    </div>
</template>

<style>
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

.task-lable {
    font-size: var(--FS-XL);
}

.line-through {
    text-decoration: line-through;
    color: #505050;
}
</style>