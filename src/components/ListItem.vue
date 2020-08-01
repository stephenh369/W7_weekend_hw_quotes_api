<template>
  <li>{{quote.author}}: <br> {{quote.en}}</li>
</template>

<script>
export default {
    name: 'list-item',
    props: ['quote']
}
</script>

<style>

</style>