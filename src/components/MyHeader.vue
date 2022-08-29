<template>
  <header>

    <img src="../assets/logo2.png" alt="">
    <div class="selezioni"> 
      <label for="cars">Seleziona genere</label>
      <select name="genere" id="genere">
        <option value="">Tutti</option>
        <option value="volvo" v-for="(genere, index) in arrayGeneriSingle" :key="index">{{genere}}</option>
      </select>
    </div>

  </header>
</template>

<script>
import axios from 'axios';
  export default {
    name:'MyHeader',

    data(){
        return{
           arrayGeneri:[],
           arrayGeneriSingle:[],
        }
    },
    created(){
      axios.get('https://flynn.boolean.careers/exercises/api/array/music')
            .then(risposta =>{
                this.arrayGeneri=risposta.data.response;
                this.listaGeneri()
            })
    },
    methods:{
            listaGeneri(){
                this.arrayGeneri.forEach((generi)=>{
                let tipo
                tipo= generi.genre
                if(!this.arrayGeneriSingle.includes(tipo)){
                    this.arrayGeneriSingle.push(tipo)
                }
            })
            },
        },

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