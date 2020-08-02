<template>
    <div>
        <ul id="fav-quotes">
            <header id="fav-quotes-header">
                <h4>Favourite Quotes</h4>
            </header>
            <quote-input/>
            <list-item v-for="quote in favouriteQuotes" :quote="quote" :key="quote.id"/>
            <list-item v-for="(ronQuote, index) in favouriteRonQuotes" :ronQuote="ronQuote" :key="index+Math.random()"/>
            <list-item v-for="(customQuote, index) in customQuotes" :customQuote="customQuote" :key="index+Math.random()"/>
        </ul>
    </div>
</template>

<script>
import { eventBus } from "@/main.js";
import ListItem from './ListItem.vue';
import QuoteInput from './QuoteInput.vue';
export default {
    name: 'favourite-quotes-list',
    props: ['favouriteQuotes', 'favouriteRonQuotes','customQuotes'],
    components: {
        'list-item' : ListItem,
        'quote-input' : QuoteInput
    }
}
</script>


<style>
    #fav-quotes {
        background-color: rgb(50,64,93,0.5);
        width: 50%;
        margin: 10% auto;
        color: #D2D4DB;
        opacity: 0.9;
        padding: 0.5rem;
        padding-top: 0;
        border-radius: 10px;
        box-shadow: 2px 2px 5px 5px rgb(50,64,93,0.5);
        list-style: none;
    }
</style>