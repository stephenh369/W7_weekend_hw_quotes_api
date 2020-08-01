<template>
  <div id="quote-input-div">
      <p>Add your own quote!:</p>
      <input id="fav-quote-input"/>
      <button class="btn">Add</button>
  </div>
</template>

<script>
import { eventBus } from "@/main.js";
export default {
    name: 'quote-input'
}
</script>

<style>
    #quote-input-div {
        display: flex;
        height: 50%;
        align-items: center;
        justify-content: space-evenly;
        margin-bottom: 25px;
    }
    #fav-quote-input {
        background-color: #242E42;
        border: 1px solid #D2D4DB;
        color: #D2D4DB;
    }
</style>