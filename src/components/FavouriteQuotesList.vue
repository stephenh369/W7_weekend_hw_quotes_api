<template>
    <div>
        <ul id="fav-quotes">
            <header id="fav-quotes-header">
                <h4>Favourite Quotes</h4>
            </header>
            <list-item v-for="(quote, index) in favouriteQuotes" :quote="quote" :key="index"/>
        </ul>
    </div>
</template>

<script>
import ListItem from './ListItem.vue';
export default {
    name: 'favourite-quotes-list',
    props: ['favouriteQuotes'],
    components: {
        'list-item' : ListItem
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