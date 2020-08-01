<template>
  <div class="flex-div">
    <li class="quote-author">{{quote.author}}:</li> 
    <li>{{quote.en}}</li>
    <button class="btn" @click="removeFavourite">Remove</button>
  </div>
</template>

<script>
import { eventBus } from "@/main.js";
export default {
    name: 'list-item',
    props: ['quote'],
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