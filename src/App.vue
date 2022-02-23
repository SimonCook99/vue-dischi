<template>
  <div id="app">
    
    <loadingState/>

    <myHeader/>
    <myMain/>
    
  </div>
</template>

<script>
import myHeader from './components/myHeader.vue'
import myMain from './components/myMain.vue'
import loadingState from "./components/loadingState.vue"

export default {
  name: 'App',
  components: {
    myHeader,
    myMain,
    loadingState
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
