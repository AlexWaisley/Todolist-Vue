<script setup lang="ts">

import { ref, watch } from 'vue';

const property = defineProps<{
    id: number,
    lable: string,
}>();

const isDone = ref(false);
const isEdit = ref(false);
const lable = ref(property.lable);


const changeStatus = () => {
    isDone.value = !isDone.value;
};

const emits = defineEmits(['changeTaskName', 'removeTask']);

watch(property, () => {
    lable.value = property.lable;
});

</script>

<template>
    <div class="task">
        <button type="button" class="mark-btn" @click="changeStatus()">
            <div v-if="isEdit">
                <img src="../assets/icons8-edit.svg" alt="Change status">
            </div>
            <div v-else>
                <div v-if="isDone">
                    <img src="../assets/double-check-svgrepo-com.svg" alt="Change status">
                </div>
                <div v-else>
                    <img src="../assets/tick-svgrepo-com.svg" alt="Change status">
                </div>
            </div>
        </button>
        <input class="task-lable" @focus="isEdit = true;"
            @blur="emits('changeTaskName', lable, property.id); isEdit = false;" v-bind:class="{ 'line-through': isDone }"
            v-model="lable" />

        <button type="button" class="delete-btn" @click="() => emits('removeTask', property.id)">
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
    border: 0;
    background-color: var(--BG-TASK-COLOR);
    font-size: var(--FS-XL);
    display: grid;
    place-content: center;
    text-align: center;
    width: 40%;

}

.line-through {
    text-decoration: line-through;
    color: #505050;
}
</style>