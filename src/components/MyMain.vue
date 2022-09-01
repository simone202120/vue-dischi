<template>
  <main>
        <div class="container">
            <StampaCard v-for="(copertina, index) in filteredDisc" :key='index' :details="copertina"/> 
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
                arrayGeneri:[],
            }
        },

        props:{
            genreToSearch: String
        },

        computed:{

            filteredDisc(){
                if(this.genreToSearch==""){
                    return this.arrayCopertine;
                }else{
                    const arrayAlbum= this.arrayCopertine.filter(album=> {
                        if(album.genre == this.genreToSearch){
                            return true;
                        }else{
                            return false;
                        }
                    });

                    return arrayAlbum
                }
            }
        },
        created(){
            axios.get('https://flynn.boolean.careers/exercises/api/array/music')
            .then(risposta =>{
                this.arrayCopertine=risposta.data.response;
                this.loading=false;

                this.arrayCopertine.forEach(copertina => {
                    if(!this.arrayGeneri.includes(copertina.genre)){
                        this.arrayGeneri.push(copertina.genre)
                    }
                })
                this.$emit('genresReady', this.arrayGeneri);
            });
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