<script setup lang="ts">
import { computed, ref } from 'vue'

interface Task {
    name: string
    isFinished: boolean
}

const tasks = ref<Task[]>([])
const finishedTasks = computed(() => tasks.value.filter((task) => task.isFinished))
const notFinishedTasks = computed(() => tasks.value.filter((task) => !task.isFinished))

const newTaskName = ref('')

const addTask = () => {
    if (newTaskName.value === '') {
        alert('タスク名を入力してください')
        return
    }
    if (tasks.value.some((task) => task.name === newTaskName.value)) {
        alert('同じ名前のタスクが存在します')
        return
    }
    tasks.value.push({
        name: newTaskName.value,
        isFinished: false
    })
    newTaskName.value = ''
}

const finishTask = (taskName: string) => {
    tasks.value = tasks.value.map((task: Task) => {
        if (task.name === taskName) {
            return {
                ...task,
                isFinished: true
            }
        }
        return task
    })
}
</script>

<template>
    <div>
        <div>TodoList</div>
        <div>完了タスク一覧</div>
        <ul v-for="task in finishedTasks" :key="task.name">
            <li>
                <div>{{ task.name }}</div>
            </li>
        </ul>
        <div>未完了タスク一覧</div>
        <ul v-for="task in notFinishedTasks" :key="task.name">
            <li>
                <div>
                    {{ task.name }}
                    <button @click="finishTask(task.name)">
                        完了
                    </button>
                </div>
            </li>
        </ul>
    </div>
    <div>
        <label>
            タスク名
            <input v-model="newTaskName" type="text">
        </label>
        <button @click="addTask">追加</button>
    </div>
</template>

<style></style>