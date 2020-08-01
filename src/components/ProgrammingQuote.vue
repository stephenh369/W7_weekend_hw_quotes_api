<template>
  <div class="quote-div">
    <header>
      <h4>Programming Quotes</h4>
    </header>
    <p v-if="randomQuote">{{randomQuote.en}}</p>
    <br>
    <div class="flex-div">
        <p class="quote-author" v-if="randomQuote">{{randomQuote.author}}</p>
        <button class="btn" @click="addFavourite">Add To Favourites</button>
        <button class="btn" @click="anotherRandomQuote">Generate Quote</button>
    </div>
  </div>
</template>

<script>
import { eventBus } from "@/main.js";
export default {
    name: 'programming-quote',
    props: ['programmingQuotes'],
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
        },
        addFavourite() {
            eventBus.$emit('add-favourite', this.randomQuote);
        }
    }
}
</script>

<style>
    h4 {
    display: inline-block;
    text-align: center;
    color: #D2D4DB;
    border-bottom: 1px #0353A4 solid;
  }
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