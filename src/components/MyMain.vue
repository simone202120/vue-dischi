<template>
  <main>
        <div class="container">
            <StampaCard v-for="(copertina, index) in arrayCopertine" :key='index' :details="copertina"/> 
            <Loadingprogress v-if="loading" />
        </div>
        
  </main>
</template>

<script>
    import axios from 'axios';
    import StampaCard from './StampaCard.vue';
    import Loadingprogress from './Loadingprogress.vue'


    export default {
        name:'MyMain',

        components: {
            StampaCard,
            Loadingprogress,
        },
    
        
        data(){
            return{
                arrayCopertine:[],
                loading: true,
                arrayGeneri:[]
            }
        },
        created(){
            axios.get('https://flynn.boolean.careers/exercises/api/array/music')
            .then(risposta =>{
                this.arrayCopertine=risposta.data.response;
                this.loading=false;
            })
           
        },
        methods:{
            listaGeneri(){
                this.arrayGeneri.forEach(generi=>{
                    let tipo= generi.genere
                    this.arrayGeneri.push(tipo)
                })
            }
        },
    }
</script>
    
<style lang="scss" scoped>
    @import '../style/general.scss';
    
    
    main{
        background-color: $coloreScuro;
        padding-top: 40px;
        padding-bottom: 40px;
    }
   
</style>