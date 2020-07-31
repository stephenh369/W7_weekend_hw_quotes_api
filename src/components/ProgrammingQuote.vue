<template>
  <div class="quote-div">
    <p>{{randomQuote.en}}</p>
    <br>
    <div class="flex-div">
        <p class="quote-author">{{randomQuote.author}}</p>
        <button class="btn">Another Quote!</button>
    </div>
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
        text-align: center;
        box-shadow: 2px 2px 5px 5px rgb(50,64,93,0.5);
    }
    .quote-author {
        color: #0466C8;
    }
    .flex-div {
        display: flex;
        height: 50%;
        align-items: center;
        justify-content: space-around;
    }
    .btn {
        background-color: #242E42;
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