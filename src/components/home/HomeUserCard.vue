<script setup lang="ts">
import BaseButton from '@/components/base/BaseButton.vue'

defineProps<{
  item: {
    login: string
    avatarUrl: string
  }
}>()
</script>

<template>
  <div class="flex flex-col justify-center items-center text-center border border-gray-300 p-5">
    <img :src="item.avatarUrl || '/placeholder.png'" class="w-16 h-16 rounded-full" />
    <h4 class="my-2.5">{{ item.login }}</h4>
    <RouterLink :to="`/users/${item.login}`" v-slot="{ href, navigate }" custom>
      <BaseButton
        is="a"
        :href="href"
        class="min-w-[100px] p-2 bg-black hover:bg-black/80 text-white"
        @click="navigate"
      >
        More
      </BaseButton>
    </RouterLink>
  </div>
</template>
