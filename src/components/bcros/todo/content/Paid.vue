<script setup lang="ts">
defineProps({
  inProcessFiling: { type: Number, required: true },
  todoItem: { type: Object as PropType<TodoItemI>, required: true }
})
</script>

<template>
  <!-- paid filing -->
  <div>
    <span>{{ $t('text.todoItem.status.pending') }}</span>
    <BcrosDivider class="mx-2" />
    <span v-if="inProcessFiling === todoItem.filingId">{{ $t('text.todoItem.status.processing') }}...</span>
    <span v-else>{{ $t('text.todoItem.status.paid') }}</span>
  </div>
</template>

<style lang="scss" scoped>
</style>
