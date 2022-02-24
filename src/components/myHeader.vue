<template>
  <header>
    <img src="../assets/logo-small.svg" alt="logo Spotify">

    <select>
      <option v-for="(genere, index) in listaGeneri" :key="index" :value="genere">{{genere}}</option>
    </select>
  </header>
</template>

<script>
export default {
  name: 'myHeader',
  props: ["listaGeneri"]
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  header{
    height: 70px;
    background-color: #2e3a46;
    display: flex;
    justify-content: space-between;
    align-items: center;

    select{
      height: fit-content;
      margin-right: 20px;
    }

    img{
      max-height: 65%;
      margin: 10px;

      //codice trovato online per settare il colore verde di un svg
      filter: invert(48%) sepia(79%) saturate(2476%) hue-rotate(86deg) brightness(118%) contrast(119%);
    }
  }
</style>
