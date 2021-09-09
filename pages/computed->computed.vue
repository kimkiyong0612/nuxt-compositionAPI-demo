<template>
  <v-card-text>
    <ul>
      <li v-for="u in data.users" :key="u.id">{{ u.id }} {{ u.name }}</li>
    </ul>
    <p>ユーザー件数: {{ userNum }}</p>
  </v-card-text>
</template>

<script lang="js">
import { defineComponent, reactive, computed } from '@nuxtjs/composition-api'

export default defineComponent({
  setup() {
    const data = reactive({
      users: [
        { id: 1, name: 'ドラえもん' },
        { id: 2, name: 'のび太くん' },
        { id: 3, name: 'しずかちゃん' },
        ],
    })
    const userNum = computed(() => data.users.length)
    return {
      data,
      userNum,
    }
  },
})
</script>
