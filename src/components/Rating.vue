<template>
  <div>
    <input type="range" min="0" max="100"
           :value="modelValue"
           @input="$emit('update:modelValue', parseInt($event.target.value))"
    >
  </div>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue'

export default defineComponent({
  name: 'Rating',
  emits: {
    'update:modelValue' (val: number | null) {
      if (val === null) {
        return true
      } else if (val && val >= 0 && val <= 100) {
        return true
      }
      return false
    }
  },
  props: {
    modelValue: {
      type: Number as PropType<number | null>
    }
  }
})
</script>
