<template>
  <div class="quote-div">
    <p>{{randomQuote.en}}</p>
    <br>
    <p class="quote-author">{{randomQuote.author}}</p>
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
    .quote-div {
        background-color: rgb(50,64,93,0.5);
        width: 50%;
        margin: auto;
        color: #D2D4DB;
        opacity: 0.9;
        padding: 0.5rem;
        border-radius: 10px;
    }
    .quote-author {
        color: #0466C8;
    }
</style>