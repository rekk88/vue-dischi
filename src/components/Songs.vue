<template>
  <div class="songs_wrap text-center">
      <div class="row gx-0">
          <div v-for="(element,index) in songList" :key="index" class="col">
             <Song :canzone="element"/>
          </div>

      </div>
  </div>
</template>

<script>
import axios from 'axios'
import Song from './Song'

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
        }
    }
}
</script>

<style lang="scss" scoped>

</style>