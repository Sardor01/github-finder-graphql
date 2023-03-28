<script setup lang="ts">
withDefaults(
  defineProps<{
    is?: 'a' | 'button'
    centered?: boolean
    disableButton?: boolean
  }>(),
  {
    is: 'button',
    centered: true
  }
)
</script>

<template>
  <component
    :is="is"
    class="inline-flex select-none items-center whitespace-nowrap text-sm font-medium uppercase transition-colors duration-150 ease-in-out focus:outline-none focus-visible:ring"
    :class="[
      centered && 'justify-center text-center',
      disableButton && 'pointer-events-none opacity-80'
    ]"
  >
    <slot />
  </component>
</template>
