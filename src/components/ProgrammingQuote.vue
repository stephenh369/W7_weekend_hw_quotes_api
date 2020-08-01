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

</style>