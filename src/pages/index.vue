<template>
  <div>
    <h1>RefEmitWithCompositionAPI</h1>
    <p>{{ message }}</p>
  </div>
</template>

<script lang="ts">
import { defineComponent } from '@vue/composition-api'

export default defineComponent({
  setup() {
    const message = 'hogehoge'
    return {
      message
    }
  }
})
</script>
