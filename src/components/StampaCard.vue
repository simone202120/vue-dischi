<template>
  
    <div class="cardDisco">
        <img :src="details.poster" alt="">
        <h4>{{details.title}}</h4>
        <p class="author">{{details.author}}</p>
        <p class="anno">{{details.year}}</p>
    </div> 

</template>

<script>
    
    export default {
        name:'StampaCard',
        props:{
            details:Object
        }
    }
</script>

<style lang="scss" scoped>

    @import '../style/general.scss';

    img{
     width: 100%;
    }
    .cardDisco{
        text-align: center;
        width: calc(85% / 5);
        margin:10px 10px;
        background-color: $coloreChiaro;
        padding: 15px;

        h4{
            color:white;
            text-transform: uppercase;
            margin-top: 10px;
        }

        .author{
            color:#707a7e;
            margin-top:20px;
            font-size: 16px;
            }

        .anno{
            color: #707a7e;
            font-size: 13px;
        }
    }

</style>