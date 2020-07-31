<template>
  <div class="quote-div">
    <p>{{randomQuote.en}}</p>
  </div>
</template>

<script>
export default {
    name: 'programming-quote',
    props: ['programmingQuotes'],
    computed: {
        randomQuote() {
            const array = this.programmingQuotes;
            return array[Math.floor(Math.random() * array.length)];
        }
    }
}
</script>

<style>

</style>