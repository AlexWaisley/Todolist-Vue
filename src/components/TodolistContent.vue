<script setup lang="ts">
import task from './Task.vue';

const property = defineProps(['tasksList']);

const emits = defineEmits(['changeTaskNameEvent', 'changeTaskIsDoneStatusEvent', 'deleteTaskEvent']);

</script>

<template>
    <div class="todolist-content">
        <task v-for="(item, index) in   property.tasksList" :id="index" :name="item.name" :is-done="item.isDone"
            @changeNameEvent="(newName, id) => emits('changeTaskNameEvent', newName, id)"
            @changeIsDoneStatusEvent="(id: number) => { emits('changeTaskIsDoneStatusEvent', id) }"
            @removeEvent="(id) => { emits('deleteTaskEvent', id); }">
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