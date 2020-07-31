<template>
  <div id="app">
    <header>
      <h2>Random Quotes</h2>
    </header>
    <programming-quote :programmingQuotes="programmingQuotes"/>
  </div>
</template>

<script>
import ProgrammingQuote from './components/ProgrammingQuote.vue';

export default {
  name: 'App',
  data() {
    return {
      programmingQuotes: []
    }
  },
  mounted() {
    this.getProgrammingQuotes();
  },
  components: {
    'programming-quote' : ProgrammingQuote
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
