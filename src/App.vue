<script setup lang="ts">
import { ref } from 'vue';

const taskList = ref(["New task"]);

taskList.value.push("New task1");
taskList.value.push("New task2");
taskList.value.push("New task3");
taskList.value.push("New task4");

</script>

<template>
    <div class="app-container">
        <header class="app-top">
            <span class="app-top-name">Todo APP</span>
            <div class="app-top-add-task-container">
                <input type="text" class="add-task-name" placeholder="Enter new task..."/>
                <button type="button" class="add-btn">
                    <img src="./assets/plus.svg" alt="">
                </button>
            </div>
        </header>
        <main class="app-main">
            <div class="task" v-for="task in taskList">
            <button type="button" class="mark-btn">
                <img src="./assets/tick-svgrepo-com.svg" alt="Change status">
            </button>
            <div class="task-lable">{{task}}</div>
            <button type="button" class="delete-btn">
                <img src="./assets/delete.svg" alt="Delete">
            </button>
            </div>
        </main>
        <footer class="app-bottom">
            <div class="tasks-count">
                <span class="tasks-count-text">{{ taskList.length }} Task{{ taskList.length !== 1 ? "s":"" }} remaining</span>
            </div>
            <button type="button" class="tasks-clear-btn">Clear all</button>
        </footer>
</div>
</template>

<style scoped>
.app-container{
    width: 600px;
    height: 850px;
    border-radius: 45px;
    box-shadow: 2px 2px 2px 2px rgba(0, 0, 0, 0.25);
    background-color: var(--BG-COLOR);
    display: grid;
    grid-template-rows: 25% 55% 20%;
    place-content: center;
}

.app-top{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}
.app-top-name{
    font-size: var(--FS-XL);
}
.app-top-add-task-container{
    display: flex;
    gap: 10px;
    justify-content: center;
    align-items: center;
}
.add-btn{
    width: 100px;
    height: 100px;
    display: grid;
    border-radius: 5px;
    place-content: center;
    background-color: var(--BTN-BG-COLOR);
    box-shadow: 2px 2px 2px 2px rgba(0, 0, 0, 0.25);
}
.add-btn:hover{
    cursor: pointer;
    background-color: var(--BTN-BG-COLOR-HOVER);
}
.add-task-name{
    height: 100px;
    width: 320px;
    font-size: var(--FS-XL);
    border-radius: 5px;
    box-shadow: 2px 2px 2px 2px rgba(0, 0, 0, 0.25);
    padding: 0 10px 0 10px;
}

.app-bottom{
    display: flex;
    justify-content: space-around;
    align-items: center;
}

.tasks-count-text{
    font-size: var(--FS-XL);
}

.tasks-clear-btn{
    width: 200px;
    height: 100px;
    font-size: var(--FS-XL);
    box-shadow: 2px 2px 2px 2px rgba(0, 0, 0, 0.25);
    display: grid;
    place-content: center;
    border-radius: 5px;
    background-color: var(--BTN-CLEAR-ALL-COLOR);
}
.tasks-clear-btn:hover{
    cursor: pointer;
    background-color: var(--BTN-CLEAR-ALL-COLOR-HOVER);
}

.app-main{
    display: flex;
    flex-direction: column;
    overflow-y: auto;
    align-items: center;
    gap: 15px;
    width: 500px;
}

.task{
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

.task-lable{
    font-size: var(--FS-XL);
}

</style>
