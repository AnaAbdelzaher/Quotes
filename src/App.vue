<template>
  <div class="container">
    <app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-header>
    <appNewQuote @quoteAdded="newQuote"></appNewQuote>
    <app-quote-grid :quotes="quotes" @quoteDeleted="deleted">

    </app-quote-grid>
    <div class="row">
            <div class="col-sm-12 text-center">
                <div class="alert alert-info">Info: Click on a Quote to delete it!</div>
            </div>
    </div>
  </div>
</template>

<script>
import QuoteGrid from './components/QuoteGrid.vue';
import NewQuote from './components/NewQuote.vue';
import Header from './components/Header.vue';


export default {
    data:function(){
      return {
        quotes:[
          "Just a Quote to see some thing"
        ],
        maxQuotes:10

    }
  },
  methods:{
    newQuote(quote){
      if (this.quotes.length >= this.maxQuotes) {
          return alert('Please delete Quotes first!');
      }
      this.quotes.push(quote);
    },
    deleted(index){
      this.quotes.splice(index,1);
    }

  },
  components:{
      appQuoteGrid:QuoteGrid,
      appNewQuote:NewQuote,
      appHeader:Header

  }
}
</script>

<style>

</style>
