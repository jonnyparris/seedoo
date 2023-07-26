<script lang="ts" setup>
defineProps(['task'])
</script>

<template>
  <div class="flex">
    <input type="checkbox" :name="task.id" :id="task.id">
    <label class="ml-2" :for="task.id">{{ task.content }}</label>
  </div>
</template>

<style lang="scss" scoped></style>
