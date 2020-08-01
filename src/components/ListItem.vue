<template>
  <div class="flex-div">
    <li class="quote-author">{{quote.author}}:</li> 
    <li>{{quote.en}}</li>
    <button class="btn">Remove</button>
  </div>
</template>

<script>
export default {
    name: 'list-item',
    props: ['quote']
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