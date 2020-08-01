<template>
    <ul>
        <list-item v-for="(quote, index) in favouriteQuotes" :quote="quote" :key="index"/>
    </ul>
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

</style>