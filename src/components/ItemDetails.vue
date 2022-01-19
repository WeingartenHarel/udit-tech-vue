<template>
  <section class="pop-up">
    <div  class="close-pop-up" @click="toggleShowItem(null)"> X </div>
    <div>Hello World item :</div>
        <p>exchange: <span>{{ item.exchange }}</span></p>
        <p>exchangeDataDelayedBy: <span>{{ item.exchangeDataDelayedBy }}</span></p>
        <p>exchangeTimezoneName: <span>{{ item.exchangeTimezoneName }}</span></p>
        <p>exchangeTimezoneShortName: <span>{{ item.exchangeTimezoneShortName }}</span> </p>
        <p>market: <span>{{ item.market }}</span>
        <p>regularMarketPrice <span>{{ item.regularMarketPrice }}</span> </p>
        <p>regularMarketpriceHint: <span>{{ item.priceHint }}</span> </p>
        <p>quoteSourceName: <span>{{ item.quoteSourceName }}</span> </p>
        <p>quoteType: <span>{{ item.quoteType }}</span></p>
        <p>region: <span>{{ item.region }}</span></p>
        <p>regularMarketChange: <span>{{ item.regularMarketChange }}</span></p>
        <p>regularMarketChangePercent: <span>{{ item.regularMarketChangePercent }}</span></p>
        <p>regularMarketPreviousClose: <span>{{ item.regularMarketPreviousClose }}</span></p>
        <p>shortName: <span>{{ item.shortName }}</span></p>
        <p>sourceInterval: <span>{{ item.sourceInterval }}</span></p>
        <p>symbol: <span>{{ item.symbol }}</span></p>
        <p>tradeable: <span>{{ item.tradeable }}</span></p>
        <p>triggerable: <span>{{ item.triggerable }}</span></p>
  </section>
</template>

<script>
export default {
  props: {
    item: {},
  },
  data() {
    return {
     
    };
  },
  methods: {
   toggleShowItem(item){
      // console.log(item)
      this.$emit('emitToggleItemDetail',item);
    }
  },
  async created() {
    console.log("hey item",this.item);
  },
};
</script>

<style>
.pop-up{
    display: flex;
    flex-direction: column;
    width: 100%;
    max-width: 500px;
    height: auto;
    position: fixed;
    padding: 1%;
    background-color: #90bbe7;
    border-radius: 20px;
    top: 20%;
}
.title {
  font-weight: 900;
  font-size: 24px;
}
.items {
  display: flex;
  gap: 30px;
  flex-wrap: wrap;
}
.item {
  width: 100%;
  max-width: 300px;
  height: auto;
  border: 1px solid black;
  background: rgb(173, 173, 173);
  list-style: none;
  padding: 20px;
  display: flex;
  flex-direction: column;
  gap: 5px;
}
p {
  font-weight: 700;
  padding: 0;
  margin: 0 0 10px 0;
}

span {
  font-weight: 400;
}
.close-pop-up{
    font-size: 24px;
    color: aliceblue;
    font-weight: 900;
    position: absolute;
    right: 30px;
}
</style>