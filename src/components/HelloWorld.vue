<script setup lang="ts">
import TodoList from './TodoList.vue'

defineProps<{
  msg: string
}>()
</script>

<template>
  <div class="greetings">
    <h1>{{ msg }}</h1>
    <TodoList />
  </div>
</template>
