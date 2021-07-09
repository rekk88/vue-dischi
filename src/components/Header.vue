<template>
  <div class="header_wrap d-flex align-items-center justify-content-between">
      <div class="logo">
          <img class="p-2" src="../assets/images/logo.png" alt="spotify logo">
      </div>
      <Select />
      
  </div>
</template>
<script>
import Select from './Select.vue'
export default {
    name:"Header",
    components:{
        Select,
    }
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