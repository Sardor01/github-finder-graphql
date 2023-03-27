<script setup lang="ts">
import { useQuery } from 'villus'

const TestQuery = `
  query TestQuery {
    search(query: "sardor01", type: USER, first: 10) {
      edges {
        node {
          ... on User {
            login
            followers {
              totalCount
            }
          }
        }
      }
    }
  }
`

interface TestI {
  search: {
    edges: {
      node: {
        login: string
        followers: {
          totalCount: number
        }
      }
    }[]
  }
}

const { data } = useQuery<TestI>({
  query: TestQuery
})
</script>

<template>
  <main class="container mx-auto py-4">
    <div v-if="data">
      <pre>{{ data.search }}</pre>
    </div>
  </main>
</template>
