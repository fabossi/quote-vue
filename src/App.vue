<template>
  <div class="container">
    <app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-header>
    <app-new-quote @quoteAdded="newQuote"></app-new-quote>
    <app-quote-grid :quotes="quotes" @quoteDeleted="deleteQuote"></app-quote-grid>
    <div class="row">
      <div v-if="quotes.length > 0" class="col-sm-12 text-center">
        <div class="alert alert-info">Info: Click on a quote to delete it!</div>
      </div>
    </div>
  </div>
</template>

<script>
import QuoteGrid from "./components/QuoteGrid.vue";
import NewQuote from "./components/newQuote.vue";
import Header from "./components/Header.vue";

export default {
  data() {
    return {
      quotes: ["Just a quote"],
      maxQuotes: 10
    };
  },
  methods: {
    newQuote(quote) {
      if (this.quotes.length >= this.maxQuotes) {
        return alert("Please, delete quotes first!");
      }
      this.quotes.push(quote);
      return;
    },
    deleteQuote(i) {
      this.quotes.splice(i, 1);
    }
  },
  components: {
    appQuoteGrid: QuoteGrid,
    appNewQuote: NewQuote,
    appHeader: Header
  }
};
</script>

<style>
</style>
