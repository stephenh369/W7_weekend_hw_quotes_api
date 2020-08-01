<template>
  <div id="quote-input-div">
      <p>Add your own quote!:</p>
      <input id="fav-quote-input" required type="text" ref="input"/>
      <button class="btn" @click="addCustomQuote($refs.input)">Add</button>
  </div>
</template>

<script>
import { eventBus } from "@/main.js";
export default {
    name: 'quote-input',
    data() {
        return {
            customQuote: ''
        }
    },
    mounted() {
    },
    methods: {
        addCustomQuote(e) {
            this.customQuote = e.value
            e.value = ''
            eventBus.$emit('add-custom-quote', this.customQuote);
            return;
        }
    }
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