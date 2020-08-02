<template>
  <div class="flex-div">
    <li class="quote-author" v-if="quote">{{quote.author}}:</li> 
    <li v-if="quote">{{quote.en}}</li>
    <li v-if="ronQuote" class="quote-author">Ron Swanson:</li>
    <li v-if="ronQuote">{{ronQuote}}</li>
    <li v-if="customQuote">{{customQuote}}</li>
    <button class="btn" v-if="quote" @click="removeFavourite">Remove</button>
    <button class="btn" v-if="ronQuote" @click="removeRonFavourite">Remove</button>
    <button class="btn" v-if="customQuote" @click="removeCustom">Remove</button>
  </div>
</template>

<script>
import { eventBus } from "@/main.js";
export default {
    name: 'list-item',
    props: ['quote', 'ronQuote','customQuote'],
    methods: {
        removeFavourite: function() {
            eventBus.$emit("favourite-removed", this.quote);
        },
        removeRonFavourite: function() {
            eventBus.$emit("favourite-ron-removed", this.ronQuote);
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