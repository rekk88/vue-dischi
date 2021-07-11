<template>
    <select name="" id="" class="mx-2" v-model="selected" @change="getValue(selected)">
          <option v-for="(gen,index) in generi" :key="index" :value="gen">{{gen}}</option>
          
    </select>
</template>

<script>

import {eventBus} from '../main.js'

export default {
    name:'Select',
    data() {
        return {
            test :"variabile test",
            canzoni:[],
            generi:[],
            selected:""
        }
    },
    created(){
        //da questo lato $on si mette in attesa del bus "songs"
        // this.canzoni = element; con questo passaggio salvo il contenuto
        //dell'autobus in una variabile interna al component
        this.getSongs()
    },
    methods:{
        getSongs(){
            eventBus.$on('songs', element =>{
                // this.canzoni = element;
                // console.log(element2);

                // console.log(this.canzoni);
                console.log(element);
                this.canzoni = element.a;
                this.generi = element.b
            });

        },
        getValue(){
            console.log("value changed in select", this.selected);
            eventBus.$emit('filtro',this.selected)
        }
    
    }
}
</script>

<style lang="scss" scoped>

</style>