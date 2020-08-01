<template>
  <div id="app">
    <header>
      <h2>Random Quotes</h2>
    </header>
    <programming-quote :programmingQuotes="programmingQuotes"/>
    <favourite-quotes-list :favouriteQuotes="favouriteQuotes"/>
  </div>
</template>

<script>
import { eventBus } from "@/main.js";
import ProgrammingQuote from './components/ProgrammingQuote.vue';
import FavouriteQuotesList from './components/FavouriteQuotesList.vue';

export default {
  name: 'App',
  data() {
    return {
      programmingQuotes: [],
      favouriteQuotes: []
    }
  },
  mounted() {
    this.getProgrammingQuotes();
    eventBus.$on('add-favourite', (favourite) => this.favouriteQuotes.push(favourite));

  },
  components: {
    'programming-quote' : ProgrammingQuote,
    'favourite-quotes-list' : FavouriteQuotesList
  },
  
  methods: {
    getProgrammingQuotes() {
    fetch('https://programming-quotes-api.herokuapp.com/quotes/lang/en')
    .then(response => response.json())
    .then(data => this.programmingQuotes = data)
    }
  }
}
</script>

<style>
  * {
    font-family: 'Playfair Display', serif;
    box-sizing: border-box;
  }
  
  header {
    text-align: center;
  }
  header > h2 {
    display: inline-block;
    text-align: center;
    color: #D2D4DB;
    border-bottom: 3px #0353A4 solid;
  }
  body {
    background-color: #242E42;
  }
</style>
