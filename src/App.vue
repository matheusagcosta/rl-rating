<template>
  <div style="padding-left: 2rem;">
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
    <div class="d-flex" style="background-color: #ededed; padding: 2rem; max-width: 60ch;">
      <div>
        Rating
      </div>
      <rating
        v-model="rating"
      ></rating>
    </div>
    <p v-if="rating === null">
      No rating
    </p>
    <p v-else>
      Current rating is {{ rating }}
    </p>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import Rating from './components/Rating.vue'

export default defineComponent({
  name: 'App',
  data () {
    return {
      rating: 42
    }
  },
  components: {
    Rating
  }
})
</script>

<style lang="scss">

body {
  line-height: 1.6;
}

p, ul {
  max-width: 60ch;
}

.d-flex {
  display: flex;
  align-items: center;

  > * {
    margin-right: 1rem;
  }
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
