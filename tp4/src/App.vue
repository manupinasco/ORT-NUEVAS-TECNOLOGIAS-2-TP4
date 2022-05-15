<template>
  <div class="container-fluid mt-3">
    <div class="jumbotron">
      <h1>TP4</h1>

      <br>

      <Navegador />
      <router-view></router-view>
      
    </div>
  </div> 
</template>

<script>
import Navegador from './components/Navegador.vue'

export default {
  name: 'App', 
  components: {
    Navegador
  }
}
</script>

<style scoped lang="scss">
  h1 {
    font-size: 34px;
    font-weight: bold;
    font-variant: small-caps;
    font-family: monospace;
    letter-spacing: 4px;
    color: black;
    text-align:center;
  }

  .jumbotron {
    background-color: rgba(0, 163, 150, 0.192);
  }
  

</style>

