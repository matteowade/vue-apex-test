<template>
  <div>
    <header>
      <div class="header-container">
        <h1>UpMetrics Code Challenge</h1>
        <a href="https://github.com/matteowade/vue-apex-test" target="_blank">View code on Github</a>
      </div>
    </header>
    <section class="container">
      <div class="inner-container">
        <studentMetrics></studentMetrics>
        <div class="dash-body-row">
          <salesOverTime class="graph-box full-width"></salesOverTime>
        </div>
        <div class="dash-body-row">
          <regionProfit class="graph-box half-width"></regionProfit>
          <regionUnitSales class="graph-box half-width"></regionUnitSales>
        </div>
        <div class="dash-body-row">
          <studentConfidence class="graph-box full-width"></studentConfidence>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import StudentMetrics from './StudentMetrics.vue'
import SalesOverTime from './SalesOverTime.vue'
import RegionProfit from './RegionProfit.vue'
import RegionUnitSales from './RegionUnitSales.vue'
import StudentConfidence from './StudentConfidence.vue'

export default {
  name: 'Dashboard',
  components: {
    studentMetrics: StudentMetrics,
    salesOverTime: SalesOverTime,
    regionProfit: RegionProfit,
    regionUnitSales: RegionUnitSales,
    studentConfidence: StudentConfidence
  }
}
</script>

<style unscoped lang="scss">
  @import '../main.scss';
</style>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  @import '../main.scss';

  header {
    border-bottom: 1px solid $brand-medium-gray;
  }

  .header-container {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    padding: 30px 40px 10px 40px;
    max-width: 1400px;
    margin: 0 auto;
  }

  .container {
    background-color: $brand-gray;
  }

  .inner-container {
    max-width: 1400px;
    padding: 40px;
    margin: 0 auto;
  }

  .dash-body-row {
    display: flex;
    flex-direction: row;
    margin-bottom: 15px;
  }

  .graph-box {
    background-color: $brand-white;
    border-radius: 10px;
    padding: 15px 30px 30px 30px;
    box-shadow: 0px 0px 30px 0px rgba(0,0,0,0.06);
    
    &.half-width {
      width: calc(50% - 15px);
      
      &:first-child {
        margin-right: 7.5px;
      }
      &:last-child {
        margin-left: 7.5px;
      }
    }
    
    &.full-width {
      width: 100%;
    }
  }
</style>
