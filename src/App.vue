<template>
  <div class="container"  >
    <app-header :quoteCount="quotes.length" :maxQuotes="maxQ" ></app-header>
    <quotes-grid
      :quotes="quotes"
      @deltedQuoteId="deleteQuote"
      ></quotes-grid>
      <new-quote @newQuote="addQuote" ></new-quote>
    <div class="row">
      <div class="col-sm-12 text-center">
          <div class="alert alert-info">
             <strong>Info:</strong> Click on a Quote to delete it!
          </div>
      </div>
    </div>
  </div>
</template>

<script>
import QuotesGrid from './components/QuoteGrid.vue'
import NewQuote from './components/NewQuote.vue'
import Header from './components/Header.vue'
export default {
  data:() => {
      return {
        quotes: ['Just a simple quote'],
        maxQ: 10,
      }
  },
  components: {
    QuotesGrid: QuotesGrid,
    newQuote: NewQuote,
    appHeader: Header,
  },
  methods: {
    addQuote(quote) {
      if (this.quotes.length >= this.maxQ) {
        alert("Please delete quotes first!")
      } else if (quote === '') {
        alert("Invalid quote!")
      } else {
        this.quotes.push(quote)
      }
    },
    deleteQuote(id) {
      this.quotes.splice(id, 1)
    }
  }

}
</script>


<style>
</style>
