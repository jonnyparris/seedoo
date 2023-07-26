<script lang="ts" setup>
import { Task, TodoistApi } from '@doist/todoist-api-typescript'

const runtimeConfig = useRuntimeConfig()

const api = new TodoistApi(runtimeConfig.todoistApiKey)

const { data: tasks } = await useAsyncData('tasks', () => {
  return api.getTasks()
})

const { data: projects } = await useAsyncData('projects', () => {
  return api.getProjects()
})

const getProjectTasks = (tasks: Task[], projectId: string) => tasks?.filter(t => t.projectId === projectId && t.parentId === null && !t.due?.isRecurring)


</script>

<template>
  <h2>Active Tasks</h2>
  <div class="flex flex-wrap">
    <Project v-show="getProjectTasks(tasks || [], project.id).length" v-for="project in projects" :key="project"
      :project="project" :tasks="getProjectTasks(tasks || [], project.id)" />
  </div>
</template>

<style lang="scss" scoped></style>
