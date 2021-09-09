<template>
  <v-card-text>  
    <div>
      <v-form
      >
        <v-text-field
          label="フォーカスがあたる"
          ref="emailInput"
        ></v-text-field>
      </v-form>
    </div>
  </v-card-text>
</template>

<script lang="js">
import { defineComponent, reactive, onMounted, ref } from '@nuxtjs/composition-api'

export default defineComponent({
  setup() {
    const emailInput = ref(null);

    onMounted(()=>{
      // this.$refs.emailInputのような形で取得していた部分
      emailInput.value.focus()
    })
    console.info("before mount", emailInput.value)

    return {
      emailInput,
    }
  },
})
</script>