<script setup lang="ts">
import GithubIcon from '@/components/icons/GithubIcon.vue'
</script>

<template>
  <header class="bg-red-500 text-white py-4">
    <div class="container mx-auto px-4">
      <RouterLink to="/" class="inline-flex items-center gap-2 text-2xl font-semibold">
        <GithubIcon width="32" height="32" />
        Github Finder
      </RouterLink>
    </div>
  </header>
</template>
