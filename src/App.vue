<template>
  <div id="app">
    
    <!--l'header monitorerà il filtragio del genere e gli verrà passata la lista generi da mostrare-->
    <myHeader @FiltraGenere="filtraGenere" :listaGeneri="listaGeneri"/>

    <!--Il main monitorerà l'evento di recupero dei generi (a seguito della chiamata axios), e gli passiamo come parametro il genere da cercare-->
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
