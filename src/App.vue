<script setup lang="ts">
import { ref } from 'vue'
import { useInfiniteScroll } from '@vueuse/core'

const data = ref([1])

useInfiniteScroll(
  document,
  () => {
    console.log('🚀 ~ file: App.vue:10 ~ document:', document)
    const length = data.value.length + 1
    data.value.push(...Array.from({ length: 5 }, (_, i) => length + i))
  },
  { distance: 100 }
)
</script>

<template>
  <div class="flex flex-col gap-2 p-4">
    <div v-for="item in data" :key="item" class="h-32 bg-gray-500/5 rounded p-3">
      {{ item }}
    </div>
  </div>
</template>
