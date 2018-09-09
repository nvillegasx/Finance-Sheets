<template>
    <div>
        
        <h3>{{ title }}</h3>

        <div class="PropertyPlantEquipment">
            <div class="row">
                <div class="column">
                    <span class="rowTitle">Land</span>
                </div>
                <div class="column2">
                    $<input type="number" name="land" v-model.number="land" placeholder="0" 
                    @keyup.enter="addItems(land,0); currVal[0].entered = true"
                    @keyup.delete="removeVal(0); currVal[0].entered = false"
                    v-bind:class="{ enterinput: currVal[0].entered }">
                </div>
            </div>
            <div class="row">
                <div class="column">
                    <span class="rowTitle">Land Improvements</span>
                </div>
                <div class="column2">
                    $<input type="number" name="landImprovements" v-model.number="landImprovements" placeholder="0" 
                        @keyup.enter="addItems(landImprovements,1); currVal[1].entered = true" 
                        @keyup.delete="removeVal(1); currVal[1].entered = false" 
                        v-bind:class="{ enterinput: currVal[1].entered}">
                </div>
            </div>
            <div class="row">
                <div class="column">
                    <span class="rowTitle">Buildings</span>
                </div>
                <div class="column2">
                    $<input type="number" name="buildings" v-model.number="buildings" placeholder="0" 
                        @keyup.enter="addItems(buildings,2); currVal[2].entered = true" 
                        @keyup.delete="removeVal(2); currVal[2].entered = false" 
                        v-bind:class="{ enterinput: currVal[2].entered}">
                </div>
            </div>
            <div class="row">
                <div class="column">
                    <span class="rowTitle">Equipment</span>
                </div>
                <div class="column2">
                    $<input type="number" name="equipment" v-model.number="equipment" placeholder="0" 
                        @keyup.enter="addItems(equipment,3); currVal[3].entered = true" 
                        @keyup.delete="removeVal(3); currVal[3].entered = false" 
                        v-bind:class="{ enterinput: currVal[3].entered}">
                </div>
            </div>
            <div class="row">
                <div class="column">
                    <span class="rowTitle">Less: Accumulated Depreciation</span>
                </div>
                <div class="column2">
                     -$<input type="number" name="accDepreciation" v-model.number="accDepreciation" placeholder="0" 
                        @keyup.enter="addItems(accDepreciation*-1,4); currVal[4].entered = true" 
                        @keyup.delete="removeVal(4); currVal[4].entered = false" 
                        v-bind:class="{ enterinput: currVal[4].entered}">
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
  name: 'PropertyPlantEquipment',
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