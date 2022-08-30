<template>
  <main>
        <div class="container">
            <StampaCard v-for="(copertina, index) in albumSelezionati" :key='index' :details="copertina"/> 
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
        genereSelezionato:"",
        components: {
            StampaCard,
            Loadingprogress,
        },
        props:{
            genereSelezionato:String
        },
        computed:{
            albumSelezionati(){
                if(this.genereSelezionato== ""){
                    return this.arrayCopertine;
                }else{
                    const copertineFiltrate =this.arrayCopertine.filter(copertina => {
                        if(copertina.genere== this.genereSelezionato){
                            return true;
                        }else{
                            return false;
                        }
                    });
                    return copertineFiltrate
                    
                }
            }
        },
        
        data(){
            return{
                arrayCopertine:[],
                loading: true,
                arrayGeneri:[],
                arrayGeneriSingle:[],
                
            }
        },
        created(){
            axios.get('https://flynn.boolean.careers/exercises/api/array/music')
            .then(risposta =>{
                this.arrayCopertine=risposta.data.response;
                this.loading=false;
            });
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
            this.$emit('genresReady', this.arrayGeneriSingle)
            
            },
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