<template>
  <header>
    <img src="../assets/logo-small.svg" alt="logo Spotify">
  </header>
</template>

<script>
export default {
  name: 'myHeader',
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  header{
    height: 70px;
    background-color: #2e3a46;

    img{
      max-height: 65%;
      margin: 10px;

      //codice trovato online per settare il colore verde di un svg
      filter: invert(48%) sepia(79%) saturate(2476%) hue-rotate(86deg) brightness(118%) contrast(119%);
    }
  }
</style>
