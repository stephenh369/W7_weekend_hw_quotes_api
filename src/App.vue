<template>
  <div id="app">
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

</style>
