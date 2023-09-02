<script setup lang="ts">
import { ref } from 'vue';

const taskName = ref('');

const emits = defineEmits(['addNewTask']);

</script>

<template>
    <span class="app-top-name">Todo APP</span>
    <div class="app-top-add-task-container">
        <input v-model="taskName" type="text" class="add-task-name" placeholder="Enter new task..." />
        <button :disabled="taskName.length === 0" type="button" class="add-btn"
            @click="emits('addNewTask', taskName); taskName = ''">
            <img src="../assets/plus.svg" alt="">
        </button>
    </div>
</template>

<style>
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
    width: var(--BTN-STNDRT-SIZE);
    height: var(--BTN-STNDRT-SIZE);
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
    width: var(--INPUT-WIDTH);
    font-size: var(--FS-XL);
    border-radius: 5px;
    box-shadow: 2px 2px 2px 2px rgba(0, 0, 0, 0.25);
    padding: 0 10px 0 10px;
}
</style>