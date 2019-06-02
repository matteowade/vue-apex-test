<template>
  <div class="hello">
    <salesOverTime></salesOverTime>
    <regionProfit></regionProfit>
    <regionUnitSales></regionUnitSales>
    <studentConfidence></studentConfidence>
  </div>
</template>

<script>
import SalesOverTime from './SalesOverTime.vue'
import RegionProfit from './RegionProfit.vue'
import RegionUnitSales from './RegionUnitSales.vue'
import StudentConfidence from './StudentConfidence.vue'

export default {
  name: 'Dashboard',
  components: {
    salesOverTime: SalesOverTime,
    regionProfit: RegionProfit,
    regionUnitSales: RegionUnitSales,
    studentConfidence: StudentConfidence
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
