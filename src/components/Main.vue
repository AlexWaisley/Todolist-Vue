<script setup lang="ts">
import task from './Task.vue';
import { watch } from 'vue';

const property = defineProps(['list']);

const emits = defineEmits(['changeName', 'changeStatus', 'deleteTask']);

watch(property.list, () => { });

</script>

<template>
    <task v-for="(item, index) in   property.list" :id="index" :lable="item.name" :status="item.isDone"
        @changeTaskName="(newName, id) => emits('changeName', newName, id)"
        @remove-task="(id) => { emits('deleteTask', id); }"
        @changeTaskStatus="(id: number) => { emits('changeStatus', id) }">
    </task>
</template>

<style></style>