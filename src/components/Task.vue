<script setup lang="ts">

import { ref, watch } from 'vue';

const property = defineProps<{
    id: number,
    lable: string,
    status: boolean
}>();

const isEdit = ref(false);
const lable = ref(property.lable);

const emits = defineEmits(['changeTaskName', 'changeTaskStatus', 'removeTask']);

watch(property, () => {
    lable.value = property.lable;

});



</script>

<template>
    <div class="task">
        <button type="button" class="default-button" @click="emits('changeTaskStatus', property.id)">
            <img v-if="isEdit" src="edit.svg" alt="Change status" />
            <img v-else-if="property.status" src="done.svg" alt="Change status" />
            <img v-else src="notDone.svg" alt="Change status" />
        </button>
        <input class="task-input" @focus="isEdit = true;" :disabled="status"
            @blur="emits('changeTaskName', lable, property.id); isEdit = false;" :class="{ 'line-through': status }"
            v-model="lable" />

        <button type="button" class="default-button" @click="() => { emits('removeTask', property.id); }">
            <img src="delete.svg" alt="Delete">
        </button>
    </div>
</template>

<style>
.task {
    max-width: 100%;
    display: flex;
    justify-content: space-between;
    height: 3rem;
    gap: 1rem;
}

.task-input {
    max-width: 15rem;
    outline: none;
    border: 1px solid transparent;
    background-color: var(--BG-COLOR);
    font-size: var(--FS-L);
    transition: border .2s;
    padding: 0 .5rem;
    display: flex;
    flex-grow: 1;
    text-align: center;
}

.task-input:focus {
    border: 1px solid #000;
}

.line-through {
    text-decoration: line-through;
    color: #505050;
}
</style>