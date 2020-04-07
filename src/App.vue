<template>
  <div class="container">
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

export default {
  data() {
    return {
      quotes: ["Just a quote"],
      maxQuotes: 10
    };
  },
  methods: {
    newQuote(quote) {
      if (quote.length > 0) {
        this.quotes.push(quote);
      }
      return;
    },
    deleteQuote(i) {
      this.quotes.splice(i, 1);
    }
  },
  components: {
    appQuoteGrid: QuoteGrid,
    appNewQuote: NewQuote
  }
};
</script>

<style>
</style>
