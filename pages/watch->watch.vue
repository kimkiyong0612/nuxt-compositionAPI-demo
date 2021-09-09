<template>
  <v-card-text>
    <form @submit.prevent>
      <div>
        <v-text-field
        label="お名前"
        type="text"
        v-model="form.name"
        />
      </div>
      <div>
        <v-text-field
        label="email"
        type="text"
        v-model="form.email"
        />
      </div>
    </form>
    </div>
  </v-card-text>
</template>

<script lang="js">
import { defineComponent, reactive, computed, ref, watch, watchEvent } from '@nuxtjs/composition-api'

export default defineComponent({
  setup() {
    const form = reactive({
      name: '',
      email: '',
    })

    watch(
      () => form.name,
      (currentName, prevName) => {
        console.info('currentName: ', currentName, 'prevName: ', prevName)
      },
    )

    return {
      form,
    }
  },
})
</script>