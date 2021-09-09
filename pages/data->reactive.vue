<template>
  <div>
    <v-card-text>
      <h1>{{ title }}</h1>
        <ul>
          <li v-for="u in data.users" :key="u.id">{{ u.id }} {{ u.name }}</li>
        </ul>
    </v-card-text>
  </div>
</template>

<script lang="js">
import { defineComponent, reactive, ref } from '@nuxtjs/composition-api'

export default defineComponent({
    setup() {
    // object declare
    const data = reactive({
        users: [
        { id: 1, name: 'ドラえもん' },
        { id: 2, name: 'のび太くん' },
        { id: 3, name: 'しずかちゃん' },
        ],
    })
    // primitive declare(internally reactive used)
    const title = ref("平和な世界")

    setTimeout(() => {
        data.users.push({ id: 4, name: 'ジャイアン' })
        title.value = "崩れた"
    }, 3000);

    return {
        data,
        title,
    }
    },
})
</script>
