<script setup lang="ts">

const property = defineProps<{
    tasksRemainTodo: Number,
}>();

const emits = defineEmits(['clearAllTasksEvent']);

</script>

<template>
    <div class="todolist-footer">
        <div class="tasks-count">
            <span class="tasks-count-text">Remaining: {{ property.tasksRemainTodo }}</span>
        </div>
        <button type="button" class="clear-tasks-button" @click="emits('clearAllTasksEvent')">Clear all</button>
    </div>
</template>

<style>
.todolist-footer {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 1rem;
}

.tasks-count-text {
    font-size: var(--FS-L);
}

.clear-tasks-button {
    outline: none;
    border: 0;
    padding: .5rem;
    height: 100%;
    font-size: var(--FS-XL);
    box-shadow: 2px 2px 2px 2px rgba(0, 0, 0, 0.25);
    display: grid;
    place-content: center;
    border-radius: 5px;
    background-color: var(--BTN-CLEAR-ALL-COLOR);
    transition: background-color .2s;
}

.clear-tasks-button:hover {
    cursor: pointer;
    background-color: var(--BTN-CLEAR-ALL-COLOR-HOVER);
}
</style>