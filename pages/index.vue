<script lang="ts" setup>
import { TodoistApi } from '@doist/todoist-api-typescript'

const runtimeConfig = useRuntimeConfig()

const api = new TodoistApi(runtimeConfig.todoistApiKey)

const { data: tasks } = await useAsyncData('todoist', () => {
  return api.getTasks()
})

</script>

<template>
  <div>
    <h2>Active Tasks</h2>
    <ul>
      <li v-for="task in tasks" :key="task.id">
        {{ task.content }}
      </li>
    </ul>
  </div>
</template>

<style lang="scss" scoped></style>
