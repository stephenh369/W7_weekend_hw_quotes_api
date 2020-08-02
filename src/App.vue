<template>
  <div id="app">
    <header>
      <h2>Random Quotes</h2>
    </header>
    <programming-quote :programmingQuotes="programmingQuotes"/>
    <ron-swanson-quote :ronSwansonQuotes="ronSwansonQuotes"/>
    <favourite-quotes-list :favouriteQuotes="favouriteQuotes" :customQuotes="customQuotes"/>
  </div>
</template>

<script>
import { eventBus } from "@/main.js";
import ProgrammingQuote from './components/ProgrammingQuote.vue';
import RonSwansonQuote from './components/RonSwansonQuote.vue';
import FavouriteQuotesList from './components/FavouriteQuotesList.vue';

export default {
  name: 'App',
  data() {
    return {
      programmingQuotes: [],
      ronSwansonQuotes: [],
      favouriteQuotes: [],
      customQuotes: []
    }
  },
  mounted() {
    this.getProgrammingQuotes();
    this.getRonSwansonQuotes();
    eventBus.$on('add-favourite', (favourite) => this.favouriteQuotes.push(favourite));
    eventBus.$on('add-custom-quote', (customQuote) => this.customQuotes.push(customQuote));
    eventBus.$on('favourite-removed', (quote) => this.favouriteQuotes.splice(this.favouriteQuotes.indexOf(quote), 1));
    eventBus.$on('custom-quote-removed', (customQuote) => this.customQuotes.splice(this.customQuotes.indexOf(customQuote), 1));
  },
  components: {
    'programming-quote' : ProgrammingQuote,
    'ron-swanson-quote' : RonSwansonQuote,
    'favourite-quotes-list' : FavouriteQuotesList,
  },
  
  methods: {
    getProgrammingQuotes() {
    fetch('https://programming-quotes-api.herokuapp.com/quotes/lang/en')
    .then(response => response.json())
    .then(data => this.programmingQuotes = data)
    },
    getRonSwansonQuotes() {
    fetch('http://ron-swanson-quotes.herokuapp.com/v2/quotes/110')
    .then(response => response.json())
    .then(data => this.ronSwansonQuotes = data)
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
  h4 {
    display: inline-block;
    text-align: center;
    color: #D2D4DB;
    border-bottom: 1px #0353A4 solid;
  }
  body {
    background-color: #242E42;
  }
  .flex-div {
    display: flex;
    height: 50%;
    align-items: center;
    justify-content: space-around;
  }
  .btn {
    background-color: #242E42;
    margin-left: 10px;
    margin-right: 10px;
    color: #D2D4DB;
    cursor: pointer;
    border: none;
    border-bottom: 1px #0353A4 solid;
    border-radius: 5px;
    padding: 5px;
  }
  .btn:hover {
    color: #0466C8;
  }
</style>
