<template>
  <div class="song_wrap">
      <div class="song">
          {{canzone.author}}
          <img :src="canzone.poster" :alt="canzone.author">
      </div>
  </div>
</template>

<script>
export default {
    name:"Song",
    props:["canzone"]
}
</script>

<style lang="scss" scoped>
    .song_wrap{
        .song{
            width: 100%;
            img{
                width: 100%
            };
        }
    }
</style>