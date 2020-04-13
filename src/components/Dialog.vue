<template>
  <v-dialog v-model="dialog" max-width="512" @click:outside="cancel">
    <v-card>
      <v-card-title>
        {{ props.title }}
      </v-card-title>
      <v-card-actions>
        <v-spacer />
        <v-btn @click="cancel">
          Cancel
        </v-btn>
        <v-btn @click="confirm">
          Confirm
        </v-btn>
      </v-card-actions>
    </v-card>
  </v-dialog>
</template>

<script lang="ts">
import { defineComponent, ref } from '@vue/composition-api'

export default defineComponent({
  props: {
    title: String
  },
  setup(props, { emit }) {
    const dialog = ref(false)

    const open = () => {
      dialog.value = true
    }
    const cancel = () => {
      dialog.value = false
      emit('cancel')
    }
    const confirm = () => {
      dialog.value = false
      emit('confirm')
    }

    return {
      props,
      dialog,
      open,
      cancel,
      confirm
    }
  }
})
</script>
