<template>
  <div class="quote-div">
    <p v-for="(quote, index) in programmingQuotes" :quote="quote" :key="index" >{{quote.en}}</p>
  </div>
</template>

<script>
export default {
    name: 'programming-quote',
    props: ['programmingQuotes']
}
</script>

<style>

</style>