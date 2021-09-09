<template>
  <v-card-text>
    <form @submit.prevent>
      <div>
        <v-text-field
          label="お名前"
          id="name"
          type="text"
          v-model="data.form.name"
        />
      </div>
      <div>
        <v-btn @click="addUser">ユーザー追加</v-btn>
      </div>
    </form>
    <div style="margin-top:16px;">
      <p>ユーザー件数: {{ userNum }}</p>
      <ul>
        <li v-for="u in data.users" :key="u.id">{{ u.id }} {{ u.name }}</li>
      </ul>
    </div>
  </v-card-text>
</template>

<script lang="js">
import { defineComponent, reactive, computed, ref } from '@nuxtjs/composition-api'

export default defineComponent({
  setup() {
    const data = reactive({
      form: {
        name: '',
      },
      users: [
        { id: 1, name: 'ドラえもん' },
        { id: 2, name: 'のび太くん' },
        { id: 3, name: 'しずかちゃん' },
      ],
    })
    const userNum = computed(() => data.users.length)
    const addUser = () => {
      if (data.form.name ==='') {
        return
      }
      const id = Math.max(...data.users.map(u=>u.id)) + 1
      data.users.push({id: id, name: data.form.name})
      data.form.name = ''
    }
    return {
      data,
      addUser,
      userNum,
    }
  },
})
</script>
