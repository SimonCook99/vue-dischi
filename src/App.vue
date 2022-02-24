<template>
  <div id="app">
    

    <myHeader :listaGeneri="listaGeneri"/>
    <myMain @listaGeneriRecuperata= "trasferisciGeneri"/>
    
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
      listaGeneri: []
    }
  },
  methods:{
    trasferisciGeneri(listaRecuperata){
      this.listaGeneri = listaRecuperata;
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
