<template>
  <div class="metric" :style="{'border-color':color}">
    <h3 class="metric-title">{{title}}</h3>
    <div class="metric-row">
      <div class="percentage">{{metric}}</div>
      <div class="trend">
        <div class="trend-icon" v-if="trend === 'up'">
          <svg version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" :style="{'fill':color}" x="0px" y="0px"
          	 viewBox="0 0 50 50" style="enable-background:new 0 0 50 50;" xml:space="preserve">
          <g><path d="M50,25c0,13.8-11.2,25-25,25S0,38.8,0,25S11.2,0,25,0S50,11.2,50,25z M23,36c0,0,0,2,2,2c2.2,0,2-2,2-2V20l5.1,4.9
          		c0,0,1.3,1.4,2.8,0c0.8-0.7,0.8-2.1,0.1-2.9l-8-7.8c0,0-1.8-2.6-4,0l-7.9,7.9c0,0-1.3,1.2,0,2.8c0,0,1.4,1.7,2.9,0.1l5-5V36z"/></g>
          </svg>
        </div>
        
        <div class="trend-icon" v-if="trend === 'down'">
          <svg version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" :style="{'fill':color}" x="0px" y="0px"
          	 viewBox="0 0 50 50" style="enable-background:new 0 0 50 50;" xml:space="preserve">
          <g><path d="M0,25C0,11.2,11.2,0,25,0s25,11.2,25,25S38.8,50,25,50S0,38.8,0,25z M27,14c0,0,0-2-2-2c-2.2,0-2,2-2,2v16l-5.1-4.9
          		c0,0-1.3-1.4-2.8,0c-0.8,0.7-0.8,2.1-0.1,2.9l8,7.8c0,0,1.8,2.6,4,0l7.9-7.9c0,0,1.3-1.2,0-2.8c0,0-1.4-1.7-2.9-0.1l-5,5V14z"/></g>
          </svg>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'MetricDisplay',
  data: function() {
    return {
    }
  },
  props: ['metric', 'title', 'trend', 'color']
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  @import '../main.scss';
  
  .metric {
    display: flex;
    flex-direction: column;
    align-items: center;
    background-color: $brand-white;
    border-radius: 10px 10px 0 0;
    border-bottom: 8px solid $brand-teal;
    padding: 30px 30px 30px 30px;
    box-shadow: 0px 0px 30px 0px rgba(0,0,0,0.06);
    margin: 0 7.5px;
    width: calc(33% - 7.5px);
    
    &:first-child {
      margin-left: 0;
      border-color: $brand-red;
    }
    
    &:last-child {
      margin-right: 0;
      border-color: $brand-blue;
    }
    
    .metric-title {
      font-size: 20px;
      font-weight: 500;
      font-family: $headline-font;
      color: lighten($brand-darkest-gray, 35%);
      margin: 0 0 10px 0;
    }
    
    .metric-row {
      display: flex;
      flex-direction: row;
      align-items: center;
      justify-content: center;
    }
    
    .percentage {
      font-family: $headline-font;
      font-size: 50px;
      font-weight: 700;
      color: $brand-darkest-gray;
    }
    
    .trend {
      .trend-icon {
        margin-left: 15px;
        svg {
          width: 40px;
          height: 40px;
        }
      }
    }
  }
</style>
