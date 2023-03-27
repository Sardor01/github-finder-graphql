<script setup lang="ts">
import { RouterView } from 'vue-router'
import { defaultPlugins, definePlugin, useClient } from 'villus'

const authPlugin = definePlugin(({ opContext }) => {
  opContext.headers.Authorization = `bearer ${import.meta.env.VITE_APP_GITHUB_GRAPHQL_AUTH_TOKEN}`
})

useClient({
  url: 'https://api.github.com/graphql',
  use: [authPlugin, ...defaultPlugins()]
})
</script>

<template>
  <RouterView />
</template>
