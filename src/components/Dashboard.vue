<template>
  <div>
    <header>
      <div class="header-container">
        <h1>UpMetrics Code Challenge</h1>
      </div>
    </header>
    <section class="container">
      <div class="inner-container">
        
        <div class="dash-body">
          <div class="dash-body-row">
            <div class="metric"></div>
          </div>
          <div class="dash-body-row">
            <salesOverTime class="graph-box"></salesOverTime>
            <regionProfit class="graph-box"></regionProfit>
          </div>
          <div class="dash-body-row">
            <regionUnitSales class="graph-box"></regionUnitSales>
            <studentConfidence class="graph-box"></studentConfidence>
          </div>
        </div>
        
      </div>
    </section>
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
<style scoped lang="scss">
  @import '../main.scss';

  header {
    border-bottom: 1px solid $brand-medium-gray;
  }
  
  .header-container {
    padding: 30px 40px 10px 40px;
    max-width: 1400px;
  }
  
  .container {
    background-color: $brand-gray;
  }
  
  .inner-container {
    max-width: 1400px;
    padding: 40px;
  }
  
  .dash-body {
    
  }
  
  .dash-body-row {
    
  }
  
  .metric {
    
  }
  
  .graph-box {
    background-color: $brand-white;
    border-radius: 10px;
    padding: 30px;
    box-shadow: 0px 0px 10px 0px rgba(0,0,0,0.05);
  }
</style>
