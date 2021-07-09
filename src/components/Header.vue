<template>
  <div class="header_wrap">
      <div class="logo">
          <img class="p-2" src="../assets/images/logo.png" alt="spotify logo">
      </div>

  </div>
</template>

<script>
export default {
    name:"Header",
}
</script>

<style lang="scss" scoped>
@import "../style/colors.scss";

.header_wrap{
    height: 70px;
    background-color: $light_blue;
    .logo{
        height: 100%;
        img{
            height: 100%
        };
    }
   
}
</style>