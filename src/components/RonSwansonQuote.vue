<template>
    <div class="quote-div">
        <header>
            <h4>Ron Swanson Quotes</h4>
        </header>
        <p v-if="randomRonQuote">{{randomRonQuote}}</p>
        <br>
        <div class="flex-div">
            <p class="quote-author" v-if="randomRonQuote">Ron Swanson</p>
            <button class="btn" @click="addRonFavourite">Add To Favourites</button>
            <button class="btn" @click="anotherRonRandomQuote">Generate Quote</button>
        </div>
    </div>
</template>

<script>
import { eventBus } from "@/main.js";
export default {
    name: 'ron-swanson-quote',
    props: ['ronSwansonQuotes'],
    data() {
        return {
            randomRonQuote: []
        }
    },
    mounted() {
        this.anotherRonRandomQuote();
    },
    methods: {
        anotherRonRandomQuote() { 
            return this.randomRonQuote = this.ronSwansonQuotes[Math.floor(Math.random() * this.ronSwansonQuotes.length)];
        },
        addRonFavourite() {
            eventBus.$emit('add-ron-favourite', this.randomRonQuote);
        }
    }
}
</script>

<style>

</style>