<template>
    <main>

        <div v-if="loading" class="loading">
            <h1>Caricamento in corso, attendere prego...</h1>
        </div>

        <!--ciclo che scorre la lista creata nella mounted, e chiama il componente myCard.vue-->
        <div v-else class="card-container">
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
        props: ["cercaGenere"],
        data(){
            return{
                songsList: [],
                filteredSongsList: [],
                listaGeneri: [],
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

                        //riempio il vettore dei generi con questo ciclo che evita di inserire valori uguali tramite includes
                        for(let i = 0; i<risposta.data.response.length; i++){
                            if(!this.listaGeneri.includes(risposta.data.response[i].genre)){
                                this.listaGeneri.push(risposta.data.response[i].genre);
                            }
                        }

                        //infine creo l'evento a cui passerò la lista aggionrata, che App.vue riceverà
                        this.$emit("listaGeneriRecuperata", this.listaGeneri);
                        console.log(this.listaGeneri);

                        console.log(this.cercaGenere);
                        /* this.filterSongs();
                        console.log(this.filteredSongsList); */

                });
            },

            filterSongs(){
                this.filteredSongsList = this.songsList.filter( item => {
                    if(item.genre.toLowerCase() == this.cercaGenere.toLowerCase()){
                        return true;
                    }else{
                        return false;
                    }
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
        text-align: center;
        position: relative;
    }

    h1{
        color: white;
        position: absolute;
        top: 40%;
        left: 50%;
        transform: translate(-50%);
    }
    .card-container{
        width: 80%;
        margin: 50px auto;

        display: flex;
        flex-wrap: wrap;
        justify-content: center;
    }
</style>