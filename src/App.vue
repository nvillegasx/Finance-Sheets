<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <div class="row">
      <div class="columnTitle">
        <h1>Balance Sheet</h1>
      </div>
    </div>
    <div class="row">
      
      <div class="column">
        <h1>Assets</h1>
        <CurrentAssets title="Current Assets"/>
        
      </div>
      <div class="column">
        <h1>Liabilities</h1>
        <CurrentLiabilities title="Current Liabilities"/>
      </div>
    </div>
    <div class="row">
      <div class="column">
        <Investments title="Investments"/>
      </div>
      <div class="column">
        <LongTermLiabilities title="Long Term Liabilities"/>
      </div>
    </div>
    <div class="row">
      <div class="column">
        <PropertyPlantEquipment title='Property Plant and Equipment'/>
      </div>
      <div class="column">
      </div>
    </div>
    <div class="row">
      <div class="column">
        <IntangibleAssets title='Intangible Assets'/>
      </div>
      <div class="column">
        <h1>Stockholders' Equity</h1>
        <StockholdersEquity/>
      </div>
    </div>
    <div class="row">
      <div class="column">
        <OtherAssets title='Other Assets'/>
      </div>
      <div class="column">
      <div class="column totalRow">
        <div class="row">
          <div class="column">
              <h3>Total Liabilities and Stockholders' Equity:</h3>
          </div>
          <div class="column2">
            <h3>$999999.99</h3>
          </div>
        </div>
      </div>
      </div>
    </div>
    <div class="row">
      <div class="column totalRow">
        <div class="row">
          <div class="column">
              <h3>Total Assets:</h3>
          </div>
          <div class="column2">
            <h3>$999999.99</h3>
          </div>
        </div>
      </div>
      <div class="column">

      </div>
    </div>
    
  </div>
</template>

<script>
import CurrentAssets from './components/CurrentAssets.vue'
import CurrentLiabilities from './components/CurrentLiabilities'
import Investments from './components/Investments'
import PropertyPlantEquipment from './components/PropertyPlantEquipment'
import IntangibleAssets from './components/IntangibleAssets'
import OtherAssets from './components/OtherAssets'
import LongTermLiabilities from './components/LongTermLiabilities'
import StockholdersEquity from './components/StockholdersEquity'


export default {
  name: 'app',
  components: {
    CurrentAssets,
    CurrentLiabilities,
    Investments,
    PropertyPlantEquipment,
    IntangibleAssets,
    OtherAssets,
    LongTermLiabilities,
    StockholdersEquity
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin-top: 60px;
}
.row {
  display: flex;
}
.column {
  flex: 50%;
}
.column2 {
  flex: 50%;
  padding-right: 15%;
  text-align: right;
}
.columnTitle {
  flex: 100%;
  text-align: center;
}
.columnTitle > h1 {
  font-size: 250%;
}
.totalRow {
    background-color: rgba(255, 255, 0, 0.808);
}
</style>
