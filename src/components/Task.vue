<script setup lang="ts">

const property = defineProps<{
    id: number,
    lable: string,
    onTaskNameChange: (name: string) => void,
    onDelete: () => void
}>();

</script>

<template>
    <div class="task">
        <button type="button" class="mark-btn">
            <img src="../assets/tick-svgrepo-com.svg" alt="Change status">
        </button>
        <div class="task-lable">{{ property.lable }}</div>
        <button type="button" class="delete-btn" @click="onDelete()">
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
</style>