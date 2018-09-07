<template>
    <div>
        
        <h3>{{ title }}</h3>

        <div class="CurrentAssets">
            <div class="row">
                <div class="column">
                    <span class="rowTitle">Cash and Cash Equivalents</span>
                </div>
                <div class="column2">
                    $<input type="number" name="cce" v-model.number="cce" placeholder="0" 
                    @keyup.enter="addItems(cce,0); currVal[0].entered = true"
                    @keyup.delete="removeVal(0); currVal[0].entered = false"
                    v-bind:class="{ enterinput: currVal[0].entered }">
                </div>
            </div>
            <div class="row">
                <div class="column">
                    <span class="rowTitle">Accounts Recievable</span>
                </div>
                <div class="column2">
                    $<input type="number" name="ar" v-model.number="ar" placeholder="0" 
                        @keyup.enter="addItems(ar,1); currVal[1].entered = true" 
                        @keyup.delete="removeVal(1); currVal[1].entered = false" 
                        v-bind:class="{ enterinput: currVal[1].entered}">
                </div>
            </div>
            <!-- FIX AFTER THIS THE INDEXEs -->
            <div class="row">
                <div class="column">
                    <span class="rowTitle">Short-Term Deposits</span>
                </div>
                <div class="column2">
                    $<input type="number" name="std" v-model.number="std" placeholder="0" 
                        @keyup.enter="addItems(std,2); currVal[2].entered = true" 
                        @keyup.delete="removeVal(std, 2); currVal[2].entered = false" 
                        v-bind:class="{ enterinput: currVal[2].entered}">
                </div>
            </div>
            <div class="row">
                <div class="column">
                    <span class="rowTitle">Marketable Securities</span>
                </div>
                <div class="column2">
                    $<input type="number" name="ms" v-model.number="ms" placeholder="0" 
                        @keyup.enter="addItems(ms,3); currVal[3].entered = true" 
                        @keyup.delete="removeVal(ms, 3); currVal[3].entered = false" 
                        v-bind:class="{ enterinput: currVal[3].entered}">
                </div>
            </div>
            <div class="row">
                <div class="column">
                    <span class="rowTitle">Work in Progress</span>
                </div>
                <div class="column2">
                    $<input type="number" name="wip" v-model.number="wip" placeholder="0" 
                        @keyup.enter="addItems(wip,4); currVal[4].entered = true" 
                        @keyup.delete="removeVal(cce, 4); currVal[4].entered = false" 
                        v-bind:class="{ enterinput: currVal[4].entered}">
                </div>
            </div>
            <div class="row">
                <div class="column">
                    <span class="rowTitle">Raw Materials</span>
                </div>
                <div class="column2">
                    $<input type="number" name="rm" v-model.number="rm" placeholder="0" 
                        @keyup.enter="addItems(rm,5); currVal[5].entered = true" 
                        @keyup.delete="removeVal(rm, 5); currVal[5].entered = false" 
                        v-bind:class="{ enterinput: currVal[5].entered}">
                </div>
            </div>
            <div class="row">
                <div class="column">
                    <span class="rowTitle">Finished Goods / Inventory</span>
                </div>
                <div class="column2">
                    $<input type="number" name="ar" v-model.number="ar" placeholder="0" @keyup.enter="addItems(ar,1); currVal[1].entered = true" 
                    @keyup.delete="removeVal(cce, 1); currVal[1].entered = false" v-bind:class="{ enterinput: currVal[1].entered}">
                </div>
            </div>
            <div class="row">
                <div class="column">
                    <span class="rowTitle">Prepaid Insurance</span>
                </div>
                <div class="column2">
                    $<input type="number" name="ar" v-model.number="ar" placeholder="0" @keyup.enter="addItems(ar,1); currVal[1].entered = true" 
                    @keyup.delete="removeVal(cce, 1); currVal[1].entered = false" v-bind:class="{ enterinput: currVal[1].entered}">
                </div>
            </div>
            <div class="row">
                <div class="column">
                    <span class="rowTitle">Prepaid Expenses</span>
                </div>
                <div class="column2">
                    $<input type="number" name="ar" v-model.number="ar" placeholder="0" @keyup.enter="addItems(ar,1); currVal[1].entered = true" 
                    @keyup.delete="removeVal(cce, 1); currVal[1].entered = false" v-bind:class="{ enterinput: currVal[1].entered}">
                </div>
            </div>
            <div class="row">
                <div class="column">
                    <span class="rowTitle">Office Supplies</span>
                </div>
                <div class="column2">
                    $<input type="number" name="ar" v-model.number="ar" placeholder="0" @keyup.enter="addItems(ar,1); currVal[1].entered = true" 
                    @keyup.delete="removeVal(cce, 1); currVal[1].entered = false" v-bind:class="{ enterinput: currVal[1].entered}">
                </div>
            </div>
            <div class="row">
                <div class="column">
                    <span class="rowTitle">Other Current Assets</span>
                </div>
                <div class="column2">
                    $<input type="number" name="ar" v-model.number="ar" placeholder="0" @keyup.enter="addItems(ar,1); currVal[1].entered = true" 
                    @keyup.delete="removeVal(cce, 1); currVal[1].entered = false" v-bind:class="{ enterinput: currVal[1].entered}">
                </div>
            </div>

            <div class="row totalRow">
                <div class="column">
                    TOTAL:
                </div>
                <div class="column finalColumn">
                    ${{ total }}
                </div>
            </div>            
        </div>
    </div>

</template>

<script>
export default {
  name: 'CurrentAssets',
  props: {
      title: String
  },
  data () {
      return {
          entered: false,
          currVal: [
              { amount: 0, entered: false },
              { amount: 0, entered: false },
              { amount: 0, entered: false },
              { amount: 0, entered: false },
              { amount: 0, entered: false },
              { amount: 0, entered: false },
              { amount: 0, entered: false },
              { amount: 0, entered: false },
              { amount: 0, entered: false },
              { amount: 0, entered: false },
              { amount: 0, entered: false }
          ],
        total: 0
      }
  },
//   Dont need a currval and prevVal just one
  methods: {
      addItems (input, index){
          this.total += input;
        //   this.prevVal[index] = input;
          this.currVal[index].amount = input;

      },
      removeVal (index){
        this.total -= this.currVal[index].amount;
        // this.prevVal[index] = 0;
        this.currVal[index].amount = 0;
      }
  }
}
</script>
<style scoped>
h1 {
    color: rgb(98, 98, 155);
}

.totalRow {
    background-color: yellow;
}

.row {
  display: flex;

}
.column {
  flex: 50%;
  padding-right: 10%;
}
.column2 {
  flex: 50%;
  padding-right: 15%;
  text-align: right;
}
.enterinput {
    background-color: rgba(43, 255, 0, 0.212);
}
input {
    text-align: right;
}
input::-webkit-inner-spin-button,
input::-webkit-outer-spin-button {
    -webkit-appearance: none;
    margin: 0;
}
.finalColumn{
    text-align: right;
    padding-right: 15%;
}
</style>