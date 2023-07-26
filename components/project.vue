<script lang="ts" setup>
defineProps(['project', 'tasks'])
</script>

<template>
  <div class="p-3 border-2 max-w-sm">
    <h3 class="font-bold uppercase pb-2">{{ project.name }}</h3>
    <ul>
      <li v-for="task in tasks" :key="task.id">
        <Task :task="task" />
      </li>
    </ul>
  </div>
</template>

<style lang="scss" scoped></style>
