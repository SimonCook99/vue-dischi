<template>
    <main>

        <!--ciclo che scorre la lista creata nella mounted, e chiama il componente myCard.vue-->
        <div class="card-container">
            <myCard v-for="(song, index) in songsList" :key="index" :song="song"/>
        </div>
    </main>
</template>

<script>

    import myCard from "./myCard.vue"

    export default {
        name: "myMain",
        components:{
            myCard
        },
        data(){
            return{
                songsList: [],
                loading: true
            }
           
        },

        methods:{
            getSongs(){
                const axios = require("axios");

                axios.get("https://flynn.boolean.careers/exercises/api/array/music")
                    .then((risposta) =>{
                        this.songsList = risposta.data.response;
                        this.loading = false;
                });
            }
        },
        mounted(){
            this.getSongs();
        }
    }
</script>

<style scoped lang="scss">

    main{
        height: calc(100vh + 120px);
    }
    .card-container{
        width: 80%;
        margin: 50px auto;

        display: flex;
        flex-wrap: wrap;
        justify-content: center;
    }
</style>