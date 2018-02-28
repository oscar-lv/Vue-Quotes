<template>
<div class="container">
  <app-header :maxQuote="maxQuotes" :quoteCount="quotes.length"></app-header>
  <new-quote @quoteAdded="newQuote">${0}</new-quote>
  <br>
  <app-quote-grid :quotes='quotes' @quoteDeleted="deleteQuote"></app-quote-grid>
  <div class="row">
    <div class="col-sm-12 text-center">
      <div class="alert alert-info"> Info: Click on a Quote to Delete it !</div>
    </div>
  </div>
</div>
</template>

<script>
import QuoteGrid from './components/QuoteGrid.vue';
import Header from './components/Header.vue';
import NewQuote from './components/NewQuote.vue';

export default {
  data: function() {
    return {
      quotes: [
        'This is the 1st quote',
      ],
      maxQuotes: 10,
    }
  },
  components: {
    appQuoteGrid: QuoteGrid,
    newQuote: NewQuote,
    appHeader : Header,

  },
  methods: {
    newQuote(quote) {
      if (this.quotes.length >= 10) {
        alert('10 quotes maximum !');
      }
      else {
        this.quotes.push(quote);
      }
    },
    deleteQuote(index) {
      this.quotes.splice(index, 1);
    }
  }
}
</script>

<style>
</style>
