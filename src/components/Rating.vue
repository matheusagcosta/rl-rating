<template>
  <div>
    <input class="rating__slider" type="range" min="0" max="100" step="25"
           :value="modelValue"
           @input="$emit('update:modelValue', parseInt($event.target.value))"
    >
    <nav class="rating__steps">
      <span class="rating__step">0</span>
      <span class="rating__step">25</span>
      <span class="rating__step">50</span>
      <span class="rating__step">75</span>
      <span class="rating__step">100</span>
    </nav>
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

<style lang="scss">
.rating {

  &__slider {
    -webkit-appearance: none;
    appearance: none;
    background-color: var(--slider-bg);
    background-image: linear-gradient(to left, #4bc67d 30%, #f1c40f 45%, #b94a48 99%);
    background-repeat: no-repeat;
    background-size: 100% 100%;
    border-radius: 10px;
    cursor: pointer;
    height: 10px;
    transition: all .1s linear;
    width: 100%;
  }

  &__steps {
    display: flex;
    justify-content: space-between;
    margin-left: -10px;
    width: calc(100% + 20px);
  }

  &__step {
    text-align: center;
    width: 30px;
  }
}

</style>
