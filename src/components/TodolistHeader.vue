<script setup lang="ts">
import { ref } from 'vue';

const taskName = ref('');

const emits = defineEmits(['addNewTask']);

</script>

<template>
    <div class="todolist-header">
        <span class="todolist-title">Todo APP</span>
        <div class="todolist-input">
            <input v-model="taskName" type="text" class="default-input" placeholder="Enter new task" />
            <button :disabled="taskName.length === 0" type="button" class="add-button"
                @click="emits('addNewTask', taskName); taskName = ''">
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

.default-input {
    display: flex;
    flex-grow: 1;
    height: 100%;
    font-size: var(--FS-L);
    outline: none;
    border: 1px dashed transparent;
    transition: border .5s;
    padding: 0 .5rem;
}

.default-input:focus {
    border: 1px dashed #000;
}

.add-button {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100%;
    border-radius: 3px;

    >img {
        max-width: 80%;
        max-height: 80%;
    }
}
</style>