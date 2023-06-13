<script setup lang="ts">
import ClickCounter from './ClickCounter.vue'

defineProps<{
  msg: string
}>()
</script>

<template>
  <div class="greetings">
    <h1>{{ msg }}</h1>
    <ClickCounter />
  </div>
</template>

<style scoped>
a {
  color: #42b983;
}
</style>
