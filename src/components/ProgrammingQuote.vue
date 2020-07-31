<template>
  <div class="quote-div">
    <p v-if="randomQuote">{{randomQuote.en}}</p>
    <br>
    <div class="flex-div">
        <p class="quote-author" v-if="randomQuote">{{randomQuote.author}}</p>
        <button class="btn" @click="anotherRandomQuote">Another Quote!</button>
    </div>
  </div>
</template>

<script>
import { eventBus } from "@/main.js";
export default {
    name: 'programming-quote',
    props: ['programmingQuotes', 'randomProgrammingQuote'],
    data() {
        return {
            randomQuote: []
        }
    },
    mounted() {
        this.anotherRandomQuote();
    },
    methods: {
        anotherRandomQuote() { 
            return this.randomQuote = this.programmingQuotes[Math.floor(Math.random() * this.programmingQuotes.length)];
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