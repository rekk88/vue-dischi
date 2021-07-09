<template>
  <div class="songs_wrap text-center d-flex justify-content-center align-items-center">
      <div class="row row-cols-5 g-0 justify-content-center">
          <div v-for="(element,index) in songList" :key="index" class="col g-3">
             
            <Song :canzone="element"/>
             
          </div>

      </div>
  </div>
</template>

<script>
import axios from 'axios'
import Song from './Song'
import {eventBus} from '../main.js'
export default {
    name:"Songs",
    components:{
        Song
    },
    data() {
        return {
            apiUrl: 'https://flynn.boolean.careers/exercises/api/array/music',
            songList : " ", //array da caricato dalla API
        }
    },
    created(){
        this.getSongs()
    },
    methods:{
        getSongs(){
            console.log(this.songList);

            axios
                .get(this.apiUrl)
                .then(risp => {
                    console.log(risp.data);
                    this.songList = risp.data.response;
                    console.log(this.songList.response);
                })
            eventBus.$on('songsMessage',(message) =>{
                console.log(message);
            })

        },
    }
}
</script>

<style lang="scss" scoped>
    .songs_wrap{
        height: calc(100vh - 70px);
    }
</style>