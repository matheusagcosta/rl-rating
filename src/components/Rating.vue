<template>
  <div class="rating__holder">
    <span class="rating__dot" v-bind:style="{ left: modelValue + '%'}"></span>
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
@mixin rating-thumb {
  -webkit-appearance: none;
  appearance: none;
  background: var(--light-color);
  border: 0px solid var(--dark-color);
  opacity: 0;
  height: 20px;
  width: 20px;
}

.rating {

  &__holder {
    display: flex;
    flex-direction: column;
    position: relative;
  }

  &__dot {
    height: 20px;
    width: 20px;
    background: var(--light-color);
    border-radius: 50%;
    box-shadow: 0 0 3px 0 rgba(0, 0, 0, .5);
    cursor: pointer;
    left: 50%;
    position: absolute;
    pointer-events: none;
    top: -3px;
    transform: translateX(-25%);
    will-change: left;
  }

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

  &__slider::-webkit-slider-thumb {
    @include rating-thumb;
  }

  &__slider::-ms-thumb {
    @include rating-thumb;
  }

  &__slider::-moz-range-thumb {
    @include rating-thumb;
  }

  &__steps {
    display: flex;
    justify-content: space-between;
    margin-left: -10px;
    padding-top: 1rem;
    width: calc(100% + 20px);
  }

  &__step {
    text-align: center;
    width: 30px;
  }

  &__step:nth-child(2) {
    transform: translateX(5%);
  }

  &__step:nth-child(3) {
    transform: translateX(10%);
  }

  &__step:nth-child(4) {
    transform: translateX(20%);
  }

  &__step:nth-child(5) {
    transform: translateX(25%);
  }
}

</style>
