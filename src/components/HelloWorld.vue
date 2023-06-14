<script setup lang="ts">
import ItemList from './TaskList.vue'

defineProps<{
  msg: string
}>()
</script>

<template>
  <div class="greetings">
    <h1>{{ msg }}</h1>
    <ItemList />
  </div>
</template>
