<script setup lang="ts">
import { onMounted, ref } from 'vue'

const goals = ref([])

const getGoals = () => {
  const url = 'http://localhost:3030/api/goals/'
  return fetch(url).then(response => response.json())
}

onMounted(() => {
  getGoals().then(data => goals.value = data)
})

</script>

<template>
  <div class="goals">
    <ul v-for="goal in goals">
      <li>{{ goal.title }}</li>
    </ul>
  </div>
</template>

<style scoped>
</style>
