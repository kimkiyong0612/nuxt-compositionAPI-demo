<template>
  <v-card-text>
    <div style="margin-top: 16px">
      <p>ユーザー件数: {{ userNum }}</p>
      <ul>
        <li v-for="u in data.users" :key="u.id">{{ u.id }} {{ u.name }}</li>
      </ul>
    </div>
  </v-card-text>
</template>

<script lang="js">
import { defineComponent, reactive, computed } from '@nuxtjs/composition-api'

export default defineComponent({
  setup() {
    const data = reactive({
      users: [],
    })

    const userNum = computed(() => data.users.length)

    // created
    console.log('created...')
    setTimeout(() => {
      data.users.push(...[
        { id: 1, name: 'ドラえもん'  },
        { id: 2, name: 'のび太くん'  },
        { id: 3, name: 'しずかちゃん' },
      ])
    }, 3000);

    return {
      data,
      userNum,
    }
  },
})
</script>