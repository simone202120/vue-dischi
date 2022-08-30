<template>
  <header>

    <img src="../assets/logo2.png" alt="">
    <div class="selezioni"> 
      <label for="cars">Seleziona genere</label>
      <select name="genere" id="genere" @change="$emit('changedGenre', SelectedGenre)"  v-model="SelectedGenre">
        <option value=" "></option>
        <option v-for="(genre, index) in genresList" :key="index" :value="genre">{{genre}}</option>
      </select>
    </div>

  </header>
</template>

<script>

  export default {
    name:'MyHeader',
    props:{
      genresList:Array
    },
   
    data(){
      return{
        SelectedGenre:""
      }
    }
  }

</script>

<style lang="scss" scoped>

  @import '../style/general.scss';

  header{
    background-color: $coloreChiaro;
    height: 70px;
    display: flex;
    justify-content: space-between;
  }
  
  img{
    height: 40px;
    margin: 15px;
  }
  .selezioni{
    margin-right: 25px;
    padding-top:20px;
    color:white;

    #genere{
      margin-left: 20px;
    }
  }

</style>