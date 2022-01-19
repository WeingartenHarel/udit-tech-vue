<template>
  <section class="">
    <div>Hello World items</div>
    <div>actions:</div>
    <input
      v-on:input="onfilterMarketList"
      v-model="filterBy.value"
      placeholder="search keyword"
    />
    <select
      @change="onfilterMarketList"
      v-model="filterBy.property"
      name="properties"
      id="properties"
    >
      <option value="exchange">exchange</option>
      <option value="exchangeTimezoneName">exchangeTimezoneName</option>
      <option value="exchangeTimezoneShortName">
        exchangeTimezoneShortName
      </option>
      <option value="market">market</option>
      <option value="regularMarketPrice">regularMarketPrice</option>
    </select>

    <ul class="items">
      <li
        class="item"
        v-for="item in marketListFilterd"
        :key="item.symbol"
        @click="toggleShowItem(item)"
      >
        <p class="title">Market details:</p>
        <p>
          exchange: <span>{{ item.exchange }}</span>
        </p>
        <p>
          exchangeTimezoneName: <span>{{ item.exchangeTimezoneName }}</span>
        </p>
        <p>
          exchangeTimezoneShortName:
          <span>{{ item.exchangeTimezoneShortName }}</span>
        </p>
        <p>
          market: <span>{{ item.market }}</span>
        </p>
        <p>
          regularMarketPrice
          <span
            >{{ item.regularMarketPrice.fmt }} |
            {{ item.regularMarketPrice.row }}</span
          >
        </p>
      </li>
    </ul>
  </section>
</template>

<script>
export default {
  props: {
    marketList: [],
  },
  data() {
    return {
      msgs: [],
      msg: { from: "", txt: "" },
      filterBy: {
        property: "exchange",
        value: null,
      },
      marketListFilterd:[],
    };
  },
  methods: {
    toggleShowItem(item) {
      this.$emit("emitShowItemDetail", item);
    },
     onfilterMarketList() {
      if (this.filterBy.property === null || this.filterBy.value === null){
         this.marketListFilterd =  this.marketList
         return;
      }
      let marketListCopy = JSON.parse(JSON.stringify(this.marketList));
      let property = this.filterBy.property.toLocaleLowerCase();
      let value = this.filterBy.value.toLocaleLowerCase();
      let result = marketListCopy.filter((item) => {
        return item[property].toLocaleLowerCase().includes(value);
      });
      this.marketListFilterd = result;
    },
  },
  computed: {
   
  },
  async created() {
    this.onfilterMarketList();
  },
};
</script>

<style>
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
</style>