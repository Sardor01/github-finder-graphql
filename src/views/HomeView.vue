<script setup lang="ts">
import { reactive, ref } from 'vue'
import { useQuery } from 'villus'
import HomeSearch from '@/components/home/HomeSearch.vue'
import AppLoading from '@/components/app/AppLoading.vue'
import HomeUserCard from '@/components/home/HomeUserCard.vue'

interface SearchUsersQuery {
  search: {
    edges: {
      node: {
        login: string
        avatarUrl: string
      }
    }[]
  }
}

const variables = reactive({
  query: '',
  first: 10
})

const SearchUsers = `
  query SearchUsers ($query: String!, $first: Int!) {
    search(query: $query, type: USER, first: $first) {
      edges {
        node {
          ... on User {
            login
            avatarUrl
          }
        }
      }
    }
  }
`

const { data, isFetching } = useQuery<SearchUsersQuery>({
  query: SearchUsers,
  variables
})

const handleQueryChange = (query: string) => {
  variables.query = query
}
</script>

<template>
  <main>
    <HomeSearch @query-change="handleQueryChange" />
    <div
      v-if="data"
      class="grid grid-cols-1 gap-4 xs:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 xl:gap-6"
    >
      <template v-if="data">
        <HomeUserCard v-for="item in data.search.edges" :key="item.node.login" :item="item.node" />
      </template>
    </div>
    <AppLoading v-if="isFetching" />
  </main>
</template>
