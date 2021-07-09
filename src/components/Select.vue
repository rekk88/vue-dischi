<template>
    <select name="" id="" class="mx-2">
          <option value="Item1">Item1</option>
          <option value="Item2">Item2</option>
          <option value="Item3">Item3</option>
    </select>
</template>

<script>

import {eventBus} from '../main.js'

export default {
    name:'Select',
    data() {
        return {
            test :"variabile test",
            canzoni:""
        }
    },
    created(){
        //da questo lato $on si mette in attesa del bus "songs"
        // this.canzoni = element; con questo passaggio salvo il contenuto
        //dell'autobus in una variabile interna al component
        
        eventBus.$on('songs', element =>{
            this.canzoni = element;
            console.log(this.canzoni);
        })
    },
    methods:{
        // getEvent(){
        //     eventBus.$emit('canzoni',this.test);
        // }
    }
}
</script>

<style lang="scss" scoped>

</style>