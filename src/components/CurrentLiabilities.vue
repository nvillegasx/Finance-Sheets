<template>
    <div>
        
        <h3>{{ title }}</h3>

        <div class="CurrentLiabilities">
            <div class="row">
                <div class="column">
                    <span class="rowTitle">Notes Payable</span>
                </div>
                <div class="column2">
                    $<input type="number" name="notesPayable" v-model.number="notesPayable" placeholder="0" 
                    @keyup.enter="addItems(notesPayable,0); currVal[0].entered = true"
                    @keyup.delete="removeVal(0); currVal[0].entered = false"
                    v-bind:class="{ enterinput: currVal[0].entered }">
                </div>
            </div>
            <div class="row">
                <div class="column">
                    <span class="rowTitle">Accounts Payable</span>
                </div>
                <div class="column2">
                    $<input type="number" name="accountsPayable" v-model.number="accountsPayable" placeholder="0" 
                        @keyup.enter="addItems(accountsPayable,1); currVal[1].entered = true" 
                        @keyup.delete="removeVal(1); currVal[1].entered = false" 
                        v-bind:class="{ enterinput: currVal[1].entered}">
                </div>
            </div>
            <!-- FIX AFTER THIS THE INDEXEs -->
            <div class="row">
                <div class="column">
                    <span class="rowTitle">Wages Payable</span>
                </div>
                <div class="column2">
                    $<input type="number" name="wagesPayable" v-model.number="wagesPayable" placeholder="0" 
                        @keyup.enter="addItems(wagesPayable,2); currVal[2].entered = true" 
                        @keyup.delete="removeVal(2); currVal[2].entered = false" 
                        v-bind:class="{ enterinput: currVal[2].entered}">
                </div>
            </div>
            <div class="row">
                <div class="column">
                    <span class="rowTitle">Interest Payable</span>
                </div>
                <div class="column2">
                    $<input type="number" name="interestPayable" v-model.number="interestPayable" placeholder="0" 
                        @keyup.enter="addItems(interestPayable,3); currVal[3].entered = true" 
                        @keyup.delete="removeVal(3); currVal[3].entered = false" 
                        v-bind:class="{ enterinput: currVal[3].entered}">
                </div>
            </div>
            <div class="row">
                <div class="column">
                    <span class="rowTitle">Taxes Payable</span>
                </div>
                <div class="column2">
                    $<input type="number" name="taxesPayable" v-model.number="taxesPayable" placeholder="0" 
                        @keyup.enter="addItems(taxesPayable,4); currVal[4].entered = true" 
                        @keyup.delete="removeVal(cce, 4); currVal[4].entered = false" 
                        v-bind:class="{ enterinput: currVal[4].entered}">
                </div>
            </div>
            <div class="row">
                <div class="column">
                    <span class="rowTitle">Warranty Liability</span>
                </div>
                <div class="column2">
                    $<input type="number" name="warrantyLiability" v-model.number="warrantyLiability" placeholder="0" 
                        @keyup.enter="addItems(warrantyLiability,5); currVal[5].entered = true" 
                        @keyup.delete="removeVal(rm, 5); currVal[5].entered = false" 
                        v-bind:class="{ enterinput: currVal[5].entered}">
                </div>
            </div>
            <div class="row">
                <div class="column">
                    <span class="rowTitle">Unearned Revenues</span>
                </div>
                <div class="column2">
                    $<input type="number" name="unearnedRev" v-model.number="unearnedRev" placeholder="0" 
                    @keyup.enter="addItems(unearnedRev,6); currVal[6].entered = true" 
                    @keyup.delete="removeVal(fgi, 6); currVal[6].entered = false" 
                    v-bind:class="{ enterinput: currVal[6].entered}">
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
  name: 'CurrentLiabilities',
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
    background-color: rgba(43, 255, 0, 0.212);
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