<template>
  <div class="hello">
    <sales></sales>
  </div>
</template>

<script>
import Sales from './Sales.vue'

export default {
  name: 'Dashboard',
  components: {
    sales: Sales
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
