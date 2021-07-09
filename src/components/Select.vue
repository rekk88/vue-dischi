<template>
    <select name="" id="" class="mx-2" @click="getEvent">
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
        eventBus.$on('songs', element =>{
            this.canzoni = element;
            console.log(this.canzoni);
        })
    },
    methods:{
        getEvent(){
            eventBus.$emit('canzoni',this.test);
        }
    }
}
</script>

<style lang="scss" scoped>

</style>