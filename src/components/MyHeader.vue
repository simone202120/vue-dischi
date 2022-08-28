<template>
  <header>

    <img src="../assets/logo2.png" alt="">

  </header>
</template>

<script>

  export default {
    name:'MyHeader'
  }

</script>

<style lang="scss" scoped>

  @import '../style/general.scss';

  header{
    background-color: $coloreChiaro;
    height: 70px;
  }
  
  img{
    height: 40px;
    margin: 15px;
  }

</style>