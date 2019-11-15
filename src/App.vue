<template>
  <div id="app">
    <Vue2/>
    <Vue3/>
  </div>
</template>

<script lang="ts">
import { Component, Vue,Model } from 'vue-property-decorator';
import Vue2 from './components/Vue2.vue';
import Vue3 from './components/Vue3.vue';

@Component({
  components: {
    Vue2,
    Vue3,
  },
})
export default class App extends Vue {
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
