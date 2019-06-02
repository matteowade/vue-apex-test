<template>
  <div id="app">
    <Dashboard/>
  </div>
</template>

<script>
import Dashboard from './components/Dashboard.vue'

export default {
  name: 'app',
  components: {
    Dashboard
  }
}
</script>

<style unscoped>
  @import 'main.scss';
</style>
