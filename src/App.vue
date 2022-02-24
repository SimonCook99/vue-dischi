<template>
  <div id="app">
    

    <myHeader @FiltraGenere="filtraGenere" :listaGeneri="listaGeneri"/>
    <myMain @listaGeneriRecuperata= "trasferisciGeneri" :cercaGenere="genereDaCercare"/>
    
  </div>
</template>

<script>
import myHeader from './components/myHeader.vue'
import myMain from './components/myMain.vue'

export default {
  name: 'App',
  components: {
    myHeader,
    myMain
  },
  data(){
    return{
      listaGeneri: [],
      genereDaCercare: ""
    }
  },
  methods:{
    trasferisciGeneri(listaRecuperata){
      this.listaGeneri = listaRecuperata;
    },
    filtraGenere(genere){
      this.genereDaCercare = genere;
      console.log(this.genereDaCercare);
    }
  }
}
</script>

<style lang="scss">
  *{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  #app{
    background-color: #1e2d3b;
  }
</style>
