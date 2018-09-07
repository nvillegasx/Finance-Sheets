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
    
  </div>
</template>

<script>
import CurrentAssets from './components/CurrentAssets.vue'
import CurrentLiabilities from './components/CurrentLiabilities'


export default {
  name: 'app',
  components: {
    CurrentAssets,
    CurrentLiabilities
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
.columnTitle {
  flex: 100%;
  text-align: center;
}
.columnTitle > h1 {
  font-size: 250%;
}
</style>
