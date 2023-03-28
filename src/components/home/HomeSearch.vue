<script setup lang="ts">
import { ref } from 'vue'
import BaseButton from '@/components/base/BaseButton.vue'

const emit = defineEmits(['queryChange'])

const query = ref('')
const handleSubmit = () => {
  emit('queryChange', query.value)
}

const handleClear = () => {
  query.value = ''
  emit('queryChange', query.value)
}
</script>

<template>
  <form class="w-full space-y-3 mb-8" @submit.prevent="handleSubmit">
    <input
      v-model="query"
      type="text"
      placeholder="Search Users..."
      required
      class="block w-full text-lg border border-gray-300"
    />
    <BaseButton type="submit" class="bg-black hover:bg-black/80 text-white w-full p-3">
      Search
    </BaseButton>
    <BaseButton
      type="button"
      class="bg-red-500 hover:bg-red-500/80 text-white w-full p-3"
      @click="handleClear"
    >
      Clear
    </BaseButton>
  </form>
</template>
