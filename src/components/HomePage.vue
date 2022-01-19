<template>
  <section class="home-page">
    <div>hello world</div>
    <div class="home-page-content">
      <ItemList
        v-if="db"
        :marketList="this.db.marketSummaryResponse.result"
        v-on:emitShowItemDetail="toggleItemDetail"
      />
      <ItemDetails
       v-if="currItem" 
       :item="this.currItem"
        v-on:emitToggleItemDetail="toggleItemDetail" 
       />
    </div>
  </section>
</template>

<script>
import { marketService } from "@/services/marketService.js";
import ItemList from "@/components/ItemList.vue";
import ItemDetails from "@/components/ItemDetails.vue";

export default {
  props: {},
  data() {
    return {
      msgs: [],
      msg: { from: "", txt: "" },
      db: null,
      currItem: null,
    };
  },
  components: {
    ItemList,
    ItemDetails,
  },
  methods: {
    toggleItemDetail(item) {
      this.currItem = item;
    },
  },
  async created() {
    const db = await marketService.query();
    this.db = db;
  },
};
</script>

<style>
.home-page {
  display: flex;
flex-direction: column;
}
.home-page-content {
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>