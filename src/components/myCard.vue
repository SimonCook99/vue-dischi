<template>
    <div class="card">
        <img :src="song.poster">
        <h2>{{song.title}}</h2>
        <p>{{song.author}}</p>
        <p>{{song.year}}</p>
    </div>
</template>

<script>
    export default {
        name:"myCard",
        props:["song"]
    }
</script>

<style scoped lang="scss">
    .card{
        width: 16%;
        background-color: #2e3a46;
        margin: 20px;
        padding: 20px;
        text-align: center;

        h2{
            color: white;
            margin-top: 20px;
            margin-bottom: 30px;
        }

        p{
            color: grey;
            
        }
        
        img{
            max-width: 100%;
        }
    }
</style>