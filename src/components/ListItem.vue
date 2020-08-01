<template>
  <div class="flex-div">
    <li class="quote-author" v-if="quote">{{quote.author}}:</li> 
    <li v-if="quote">{{quote.en}}</li>
    <li>{{customQuote}}</li>
    <button class="btn" @click="removeFavourite">Remove</button>
  </div>
</template>

<script>
import { eventBus } from "@/main.js";
export default {
    name: 'list-item',
    props: ['quote', 'customQuote'],
    methods: {
        removeFavourite: function() {
            eventBus.$emit("favourite-removed", this.quote);
        }
    }
}
</script>

<style>
    li {
        margin-bottom: 25px;
        margin-left: 5px;
        margin-right: 5px;
        text-align: center;
    }
</style>