<script setup lang="ts">
import { ref } from 'vue';

const newTaskName = ref('');

const emits = defineEmits(['addNewTaskEvent']);

</script>

<template>
    <div class="todolist-header">
        <span class="todolist-title">Todo APP</span>
        <div class="todolist-input">
            <input v-model="newTaskName" type="text" class="default-input" placeholder="Enter new task" />
            <button :disabled="newTaskName.length === 0" type="button" class="default-button"
                @click="emits('addNewTaskEvent', newTaskName); newTaskName = ''">
                <img src="plus.svg" alt="plus image">
            </button>
        </div>
    </div>
</template>

<style>
.todolist-header {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    gap: 1rem;
}

.todolist-title {
    font-size: var(--FS-XL);
    width: 100%;
    display: flex;
    justify-content: center;
}

.todolist-input {
    display: flex;
    width: 100%;
    height: 3rem;
    align-items: center;
    justify-content: center;
    gap: 1rem;
}
</style>