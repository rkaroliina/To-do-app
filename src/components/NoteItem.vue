<script lang="ts">
import type { Note } from '@/interfaces/Note'
import { defineComponent } from 'vue'
import type { PropType } from 'vue'

export default defineComponent({
  props: {
    note: {
      type: Object as PropType<Note>,
      default() {
        return { title: 'Example', description: 'This is an example note', completed: true }
      }
    }
  },
  emits: {
    remove() {
      return true
    }
  }
})
</script>

<template>
  <tr class="rounded shadow-lg">
    <td class="w-0 text-center">
      <input
        type="checkbox"
        v-model="note.completed"
        class="h-4 w-4 rounded border-gray-300 bg-gray-100 text-blue-600 focus:ring-2 focus:ring-blue-500 dark:border-gray-600 dark:bg-gray-700 dark:ring-offset-gray-800 dark:focus:ring-blue-600"
      />
    </td>
    <td>
      <input class="text-2xl" type="text" v-model="note.title" />
    </td>
    <td class="w-full">
      <input class="w-full" type="text" v-model="note.description" />
    </td>
    <td class="w-6">
      <button @click="$emit('remove')" class="btn btn-blue">Delete</button>
    </td>
  </tr>
</template>

<style>
.btn {
  @apply rounded px-4 py-2 font-bold;
}
.btn-blue {
  @apply bg-blue-500 text-white;
}
.btn-blue:hover {
  @apply bg-blue-700;
}
</style>
