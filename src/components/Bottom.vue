<script setup lang="ts">

const property = defineProps<{
    count: Number,
}>();

const emits = defineEmits(['clearAllTasks']);

</script>

<template>
    <div class="tasks-count">
        <span class="tasks-count-text">{{ property.count }} Task{{ property.count !== 1 ? "s" : "" }} remaining</span>
    </div>
    <button type="button" class="tasks-clear-btn" @click="emits('clearAllTasks')">Clear all</button>
</template>

<style>
.tasks-count-text {
    font-size: var(--FS-XL);
}

.tasks-clear-btn {
    width: 200px;
    height: 100px;
    font-size: var(--FS-XL);
    box-shadow: 2px 2px 2px 2px rgba(0, 0, 0, 0.25);
    display: grid;
    place-content: center;
    border-radius: 5px;
    background-color: var(--BTN-CLEAR-ALL-COLOR);
}

.tasks-clear-btn:hover {
    cursor: pointer;
    background-color: var(--BTN-CLEAR-ALL-COLOR-HOVER);
}
</style>