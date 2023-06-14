<script setup lang="ts">
import {ref} from 'vue'

interface Task {
    name: string
    status: boolean
}

const tasks = ref<Task[]>([
    {name: '掃除', status:true},
    {name: '勉強', status:false},
    {name: '買い物', status:false},
])
const newTaskName = ref('')

const updateStatus = (taskName: string) => {
    for (var i=0; i<tasks.value.length; i++) {
        if (tasks.value[i].name == taskName ){
            tasks.value[i].status = !tasks.value[i].status
        }
    }
}

const addTask = () => {
    tasks.value.push({name: newTaskName.value, status: false})
}
</script>

<template>
    <div>TaskList</div>
    <ul>
        <li v-for="task in tasks" :key="task.name" :class="{taskDone: task.status == true}">
            <div>
                タスク名: {{ task.name }}
                <button v-if="task.status == false" @click="updateStatus(task.name)">完了!</button>
            </div>
        </li>
    </ul>
    <div>
        <label>
            タスク名
            <input v-model="newTaskName" type="text">
        </label>
        <button @click="addTask">追加</button>
    </div>
</template>

<style>
.taskDone {
    color: lightgreen;
}
</style>