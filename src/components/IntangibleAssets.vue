<template>
    <div>
        
        <h3>{{ title }}</h3>

        <div class="IntangibleAssets">
            <div class="row">
                <div class="column">
                    <span class="rowTitle">Intangible Assets</span>
                </div>
                <div class="column2">
                    $<input type="number" name="intangibleAssets" v-model.number="intangibleAssets" placeholder="0" 
                    @keyup.enter="addItems(intangibleAssets,0); currVal[0].entered = true"
                    @keyup.delete="removeVal(0); currVal[0].entered = false"
                    v-bind:class="{ enterinput: currVal[0].entered }">
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
  name: 'IntangibleAssets',
  props: {
      title: String
  },
  data () {
      return {
          entered: false,
          currVal: [
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