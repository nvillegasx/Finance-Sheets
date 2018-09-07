<template>
    <div>
        
        <h3>{{ title }}</h3>

        <div class="CurrentAssets">
            <div class="row">
                <div class="column">
                    <span class="rowTitle">Cash and Cash Equivalents</span>
                </div>
                <div class="column">
                    <input type="number" name="cce" v-model.number="cce" placeholder="$" @change="addItems(cce)">
                    {{ cash }}
                </div>
            </div>
            <div class="row">
                <div class="column">
                    <span class="rowTitle">Accounts Recievable</span>
                </div>
                <div class="column">
                    <input type="number" name="ar" v-model.number="ar" placeholder="$" @change="addItems(ar)">
                </div>
            </div>

            <div class="row totalRow">
                <div class="column">
                    TOTAL:
                </div>
                <div class="column">
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
        items: [
            { section: 'Cash and cash Equivalents'},
            { section: 'Accounts Recievable'}
        ], 
        total: 0,
        cash: 0,
        receivables: 0
      }
  },
  methods: {
      addItems (num){
          this.total += num;
          this.cash = num;
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
}
</style>