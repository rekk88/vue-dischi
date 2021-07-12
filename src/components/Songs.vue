<template>
  <div class="songs_wrap text-center d-flex justify-content-center align-items-center">
      <div class="row row-cols-5 g-0 justify-content-center">
          <div v-for="(element,index) in songList" :key="index" class="col g-3">
             
            <Song v-if="(selectedGenre == element.genre) || (selectedGenre == 'all')" :canzone="element"/>
             <div v-else class="offset col-5"></div>
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
            filteredSongList:[],
            genreList : ["all"],
            selectedGenre: "all",
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
                    //$emit lancia un evento sul bus "songs" e passa come
                    //parametro this.songlist

                    //questo funziona ma c'è da capire perchè con filter non va
                    // for(let i=0; i < this.songList.length ; i++){
                    //     if(!this.genreList.includes(this.songList[i].genre)){
                    //         this.genreList.push(this.songList[i].genre)
                    //     }
                    // }
                    this.songList.forEach(element => {
                        if(!this.genreList.includes(element.genre)){
                             console.log("element : " , element.genre);
                             this.genreList.push(element.genre)
                        }
                    });
                    console.log("genere  : ",this.genreList);
                    eventBus.$emit('songs',{a : this.songList,b : this.genreList})
                })
            
            // eventBus.$on('songsMessage',(message) =>{
            //     console.log(message);
            // })
            eventBus.$on('filtro', element =>{
                console.log(element);
                this.selectedGenre = element;
        
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