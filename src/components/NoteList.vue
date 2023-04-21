<script lang="ts">
import type { Note, NoteArray } from '@/interfaces/Note'
import { defineComponent } from 'vue'
import type { PropType } from 'vue'
import NoteItem from '@/components/NoteItem.vue'

export default defineComponent({
  props: {
    notes: {
      type: Object as PropType<NoteArray>,
      default() {
        return []
      }
    }
  },
  methods: {
    addNote(event: Event) {
      this.notes.push({
        title: 'New Note',
        description: 'Note description.',
        completed: false
      })
    }
  },
  components: {
    NoteItem
  }
})
</script>

<template>
  <table class="table w-full table-auto">
    <thead>
      <th>Completed</th>
      <th>Title</th>
      <th>Description</th>
      <th>Edit</th>
    </thead>
    <tbody>
      <NoteItem v-for="(note, idx) in notes" :note="note" @remove="notes.splice(idx, 1)" />
      <tr>
        <td></td>
        <td></td>
        <td></td>
        <td>
          <button @click="addNote" class="btn btn-blue">Add Note</button>
        </td>
      </tr>
    </tbody>
  </table>
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
