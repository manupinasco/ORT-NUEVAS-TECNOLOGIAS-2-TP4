<template>

    <nav class="navbar navbar-dark bg-dark">
    
    <router-link to="/">
      <a class="navbar-brand" href="#">Inicio</a>
    </router-link>
    
    <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    
    <div class="collapse navbar-collapse" id="navbarNav">
      <ul class="navbar-nav">
          <li class="nav-item">

            <router-link to="/formulario">
              <a href="#" class="nav-link">Formulario</a>
            </router-link>

          </li>


        </ul>

      </div>



    </nav>

</template>

<script>

  export default  {
    name: 'src-components-navegador',
    props: [],
    mounted () {

    },
    data () {
      return {

      }
    },
    methods: {

    },
    computed: {

    }
}


</script>

<style>
  .src-components-navegador {

  }
</style>
