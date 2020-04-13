<template>
  <v-container>
    <v-row>
      <v-col cols="12">
        <v-card>
          <v-card-title>
            RefEmitWithCompositionAPI
          </v-card-title>
          <v-card-text>
            <p>
              This is a sample project for using Ref and Emit with Nuxt.js and
              CompositionAPI.
            </p>
          </v-card-text>
        </v-card>
      </v-col>
      <v-col cols="12">
        <v-card>
          <v-card-title>
            Dialog
          </v-card-title>
          <v-card-actions>
            <v-btn @click="openDialog">
              Open Dialog
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
      <v-col cols="12">
        <v-card>
          <v-card-title>
            Dialog: Result
          </v-card-title>
          <v-card-text>
            <v-alert v-show="result === null" type="info">
              undefined (or loading)
            </v-alert>
            <v-alert v-show="result === 'cancel'" type="warning">
              cancel
            </v-alert>
            <v-alert v-show="result === 'confirm'" type="success">
              confirm
            </v-alert>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script lang="ts">
import { defineComponent, ref } from '@vue/composition-api'

export default defineComponent({
  setup() {
    const result = ref(null as 'confirm' | 'cancel' | null)

    const title = 'Example Dialog'
    const openDialog = () => {
      result.value = null
    }
    const cancel = () => {
      result.value = 'cancel'
    }
    const confirm = () => {
      result.value = 'confirm'
    }

    return {
      result,
      title,
      cancel,
      confirm,
      openDialog
    }
  }
})
</script>
