<template>
  <div class="song_wrap">
          <img :src="canzone.poster" :alt="canzone.author" class="p-2">
          <div>{{canzone.author}}</div>
          <div>{{canzone.genre}}</div>
  </div>
</template>

<script>
export default {
    name:"Song",
    props:["canzone"]
}
</script>

<style lang="scss" scoped>
@import "../style/colors.scss";
    .song_wrap{
        background-color: $light_blue;
        img{
            height: 150px;
        };
        div:nth-of-type(1){
            color: white;
            font-size: 20px;
            
        };
        div:nth-of-type(2){
            color: grey;
        }

    }
</style>