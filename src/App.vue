<template>
  <main>
    <p>
      Please build a component for rating candidates. An example use case would be hiring
      managers giving their opinion on candidate fit for a position. The component should emit
      a numeric value in range [0; 100] or null, if no value is selected. The component should
      have basic styles and be fully functional. Implement the component in components/Rating.vue.
    </p>
    <ul>
      <li>Make sure the component can not emit invalid values.</li>
      <li>Feel free to include 3rd party code, if necessary.</li>
      <li>Try to keep the implementation time below 2h (excluding reading
        <a href="https://v3.vuejs.org/guide/introduction.html" target="_blank">docs</a>).
        Make necessary tradeoffs.</li>
      <li>Let's discuss if you have any questions.</li>
    </ul>
    <div class="rating">
      <label class="rating__label">Rating</label>
      <rating
        v-model="rating"
      ></rating>
    </div>
    <span class="alert" style="--alert--bg: #bf6358;" v-if="rating === 0">
      Not a Match. 💔
    </span>
    <span class="alert" style="--alert--bg: #d17e30;" v-else-if="rating === 25">
      Small Fit. 😕
    </span>
    <span class="alert" style="--alert--bg: #E6A942;" v-else-if="rating === 50">
      Intermidiate. 😐
    </span>
    <span class="alert" style="--alert--bg: #58d593;" v-else-if="rating === 75">
      Good Fit 😀
    </span>
    <span class="alert" style="--alert--bg: #00c14f;" v-else-if="rating === 100">
      Perfect Match! 🎉
    </span>
    <span class="alert" style="--alert--bg: #abb7b7;" v-else>
      No Rating yet...
    </span>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import Rating from './components/Rating.vue'

export default defineComponent({
  name: 'App',
  data () {
    return {
      rating: null
    }
  },
  components: {
    Rating
  }
})
</script>

<style lang="scss">

:root {
  --alert--bg: #abb7b7;
  --body--bg: #EFF1F4;
  --light-color: #FFF;
  --slider-bg: #888;
  --text-color: #2c3e50;
  --main-width: 600px;
}

*, ::after, ::before {
  box-sizing: border-box;
}

body {
  background-color: var(--body--bg);
  line-height: 1.6;
}

p, ul {
  max-width: var(--main-width);
}

label {
  font-weight: bold;
  margin-bottom: 1rem;
}

.rating {
  background-color: var(--light-color);
  border-radius: 10px;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  max-width: 100%;
  width: var(--main-width);
  padding: 2rem;
}

.alert {
  background: var(--alert--bg);
  border-radius: 4px;
  color: var(--light-color);
  font-weight: bold;
  display: block;
  margin-top: 1rem;
  max-width: 100%;
  padding: 1rem;
  width: var(--main-width);
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: var(--text-color);
  padding: 2rem;
}
</style>
