<script setup lang="ts">
import task from './Task.vue';
import { watch } from 'vue';

const property = defineProps(['list']);

const emits = defineEmits(['changeName', 'changeStatus', 'deleteTask']);

watch(property.list, () => { });

</script>

<template>
    <div class="todolist-content">
        <task v-for="(item, index) in   property.list" :id="index" :lable="item.name" :status="item.isDone"
            @changeTaskName="(newName, id) => emits('changeName', newName, id)"
            @remove-task="(id) => { emits('deleteTask', id); }"
            @changeTaskStatus="(id: number) => { emits('changeStatus', id) }">
        </task>
    </div>
</template>

<style>
.todolist-content {
    width: 100%;
    display: flex;
    flex-grow: 1;
    flex-direction: column;
    gap: 1rem;
    overflow-y: auto;
    padding: .5rem 0;
}
</style>