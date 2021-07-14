<template>
  <div>
    <Task
      v-for="task in tasks"
      :key="task.id"
      :task="task"
      @toggle-reminder="$emit('toggle-reminder', task.id)"
      @delete-task="$emit('delete-task', task.id)"
    />
  </div>
</template>

<script lang="ts">
import { defineComponent, PropType } from '@vue/composition-api'
import Task from '@/types/task'

export default defineComponent({
  props: {
    tasks: {
      type: Array as PropType<Task[]>,
      required: true,
    },
  },

  emits: ['toggle-reminder', 'delete-task'],
})
</script>