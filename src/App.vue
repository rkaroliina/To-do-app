<script lang="ts">
import MainNav from '@/components/MainNav.vue'
import NoteList from '@/components/NoteList.vue'
export default {
  name: 'App',
  components: {
    MainNav,
    NoteList
  },
  data() {
    return {
      notes: [
        {
          title: 'Example',
          description: 'This is an example',
          completed: false
        },
        {
          title: 'Example',
          description: 'This is an example',
          completed: false
        },
        {
          title: 'Example',
          description: 'This is an example',
          completed: false
        }
      ]
    }
  }
}
</script>

<template>
  <MainNav />
  <main class="h-full w-full">
    <NoteList :notes="notes" />
  </main>
</template>
