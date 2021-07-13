<template>
  <div>
    <AddTaskForm v-if="isShowAddTaskForm" @add-task="addTask" />

    <Tasks
      v-if="tasksRef"
      :tasks="tasksRef"
      @delete-task="deleteTask"
      @toggle-reminder="toggleReminder"
    />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from '@vue/composition-api'
import Task from '@/types/task'
import useList from '../composables/use-list'

export default defineComponent({
  props: {
    isShowAddTaskForm: Boolean,
  },

  setup() {
    const tasksRef = ref<Task[]>()
    const { load, addTask, deleteTask, toggleReminder } = useList(tasksRef)

    load()

    return {
      tasksRef,
      addTask,
      deleteTask,
      toggleReminder,
    }
  },
})
</script>