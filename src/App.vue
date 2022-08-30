<template>
  <div id="app">

    <MyHeader @changedGenere="ricercaPerGenere" :passaGeneri="listaGeneri"/>
    <MyMain @genresReady="gestioneGeneri" @genereSelezionato= genereSelezionato />

  </div>
</template>

<script>
  
  import MyHeader from './components/MyHeader';
  import MyMain from './components/MyMain.vue'

  export default {
    name: 'App',
    components: {
    MyHeader,
    MyMain,
    },

    data(){
      return{
        listaGeneri: [],
        genereSelezionato:""
      }
    },
    methods:{
      gestioneGeneri(tuttiGeneri){
        this.listaGeneri=tuttiGeneri
        console.log(this.listaGeneri)
      },
      ricercaPerGenere(genereSelezionato){
        this.genereSelezionato=genereSelezionato;
      }
    }
  }
</script>

<style lang="scss">

 @import'./style/general.scss'

</style>
