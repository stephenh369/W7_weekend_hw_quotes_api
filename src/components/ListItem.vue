<template>
  <div class="flex-div">
    <li class="quote-author" v-if="quote">{{quote.author}}:</li> 
    <li v-if="quote">{{quote.en}}</li>
    <li v-if="customQuote">{{customQuote}}</li>
    <button class="btn" v-if="quote" @click="removeFavourite">Remove</button>
    <button class="btn" v-if="customQuote" @click="removeCustom">Remove</button>
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
        },
        removeCustom: function() {
            eventBus.$emit("custom-quote-removed", this.customQuote);
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