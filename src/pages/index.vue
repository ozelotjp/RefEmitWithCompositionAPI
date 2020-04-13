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
    <Dialog ref="dialog" :title="title" @cancel="cancel" @confirm="confirm" />
  </v-container>
</template>

<script lang="ts">
import { defineComponent, ref } from '@vue/composition-api'
import Dialog from '@/components/Dialog.vue'

export default defineComponent({
  components: {
    Dialog
  },
  setup() {
    const result = ref(null as 'confirm' | 'cancel' | null)

    const dialog = ref()
    const title = 'Example Dialog'
    const openDialog = () => {
      result.value = null
      dialog.value.open(title)
    }
    const cancel = () => {
      result.value = 'cancel'
    }
    const confirm = () => {
      result.value = 'confirm'
    }

    return {
      result,
      dialog,
      title,
      cancel,
      confirm,
      openDialog
    }
  }
})
</script>
