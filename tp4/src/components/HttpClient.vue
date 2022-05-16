<template>

  <section class="src-components-http-client">
    <div class="jumbotron">
      <h1>HttpClient Component</h1>


      <br>
      <br>
      <br>

      <button class="btn btn-success my-3 mr-3" @click="getPostsXHRcb()">Pedir XHR (cb)</button>
      <button class="btn btn-success my-3 mr-3" @click="getPostsFetch()">Pedir Fetch (Promise)</button>
      <button class="btn btn-success my-3 mr-3" @click="getPostsAxios()">Pedir Axios</button>
      <button class="btn btn-success my-3 mr-3" @click="users = []">Clear</button>
      <br>

      <div v-if="users.length" class="class table-responsive">
        <table class="class table table-dark">
          <tr>
            <th>Nombre</th>
            <th>Email</th>
            <th>Número de Teléfono</th>
          </tr>
          <tr v-for="(user,index) in users" :key="index">
            <td>{{user.nombre}}</td>
            <td>{{user.email}}</td>
            <td>{{user.numTel}}</td>


          </tr>

        </table>
      </div>

      <h4 v-else class="alert alert-danger"> No se encontraron datos</h4>
    </div>
    
  </section>

</template>

<script>

  export default  {
    name: 'src-components-http-client',
    props: [],
    mounted () {

    },
    data () {
      return {
        url: 'https://627da2b8dd8aafd4fa80dcd3.mockapi.io/usuarios',
        users: []
      }
    },
    methods: {
      getPostsXHRcb() {
        const xhr = new XMLHttpRequest()
        xhr.open('get', this.url)
        xhr.addEventListener('load', () => {
          if(xhr.status == 200) {
            let respuesta = JSON.parse(xhr.response)
            this.users = respuesta
          }

        })



        xhr.send()
      },

      async getPostsFetch() {

        try {
          let response = await fetch(this.url)
          let respuesta = await response.json() 
          this.users = respuesta
        }
        catch(error) {
          console.error('Error en Fetch: ', error)
        }
        



      },

      async getPostsAxios() {

          try {
            let {data: respuesta} = await this.axios(this.url)
            console.log(respuesta)
            this.users = respuesta
          }
          catch(error) {
            console.error('Error en Axios: ', error)
          }
          
      }
    },
    computed: {

    }
}


</script>

<style>
  .src-components-http-client {

  }
  .jumbotron {
      background-color: rgb(5, 41, 43);
      color: white;
  }

</style>
