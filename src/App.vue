<template>
  <div id="app">
    <li v-for="(quote, index) in programmingQuotes" :quote="quote" :key="index">{{quote.en}}</li>
  </div>
</template>

<script>

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
