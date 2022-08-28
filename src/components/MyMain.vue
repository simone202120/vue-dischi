<template>
  <main>
        <div class="container">
            <StampaCard v-for="(copertina, index) in arrayCopertine" :key='index' :details="copertina"/> 
        </div>
  </main>
</template>

<script>
import axios from 'axios';
import StampaCard from './StampaCard.vue';


export default {
    name:'MyMain',

    components: {
    StampaCard,
    
},
   
    
    data(){
        return{
            arrayCopertine:[]
        }
    },
    created(){
        axios.get('https://flynn.boolean.careers/exercises/api/array/music')
        .then(risposta =>{
            this.arrayCopertine=risposta.data.response
        })
    }
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