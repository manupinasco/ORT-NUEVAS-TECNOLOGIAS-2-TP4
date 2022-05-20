<template>

  <section class="src-components-formulario">
    <div class="jumbotron">
      <h1>Formulario</h1>

      <br>
      <br>

      <vue-form :state="formState" @submit.prevent="enviar()">

        <validate tag="div">

          <label for="nombre">Nombre</label>
          <input 
            type="text"
            id="nombre"
            class="form-control"
            name="nombre"
            autocomplete="off"
            v-model.trim="formData.nombre" 
            required 
            :minlength="nombreMinLength"
            maximo
          />
    
          <field-messages name="nombre" show="$dirty">
            <div slot="required" class="alert alert-danger mt-1">Campo requerido</div>
            <div slot="minlength" class="alert alert-danger mt-1">
              Este campo debe poseer al menos {{nombreMinLength}} caracteres.
            </div>
            <div slot="maximo" class="alert alert-danger mt-1">
              Este campo no debe poseer más de {{nombreMaxLength}} caracteres.
            </div>
          </field-messages>

        </validate>

        <br>

        <validate tag="div">

          <label for="edad">Edad</label>
          <input 
            type="number"
            id="edad"
            class="form-control"
            name="edad"
            autocomplete="off"
            v-model.number="formData.edad" 
            required 
            :min="edadMin"
            :max="edadMax"
          />
    
          <field-messages name="edad" show="$dirty">
            <div slot="required" class="alert alert-danger mt-1">Campo requerido</div>
            <div slot="min" class="alert alert-danger mt-1">La edad mínima debe ser {{edadMin}} años.</div>
            <div slot="max" class="alert alert-danger mt-1">La edad no debe superar los {{edadMax}} años.</div>
          </field-messages>

        </validate>
        <br>

        <validate tag="div">

          <label for="email">Email</label>
          <input 
            type="email"
            id="email"
            class="form-control"
            name="email"
            autocomplete="off"
            v-model="formData.email" 
            required 
          />
    
          <field-messages name="email" show="$dirty">
            <div slot="required" class="alert alert-danger mt-1">Campo requerido</div>
            <div slot="email" class="alert alert-danger mt-1">Email no válido</div>
          </field-messages>

        </validate>
        <br>

        <button class="btn btn-success my-3" :disabled="formState.$invalid">Enviar</button>

      </vue-form>
 

      <div class="class table-responsive">
        <table class="class table table-dark">
          <tr>
            <th>Nombre</th>
            <th>Edad</th>
            <th>Email</th>
          </tr>
          <tr>
            <td> {{formFinal.nombre}}</td>
            <td>{{formFinal.edad}}</td>
            <td>{{formFinal.email}}</td>


          </tr>

      </table>
      </div>
  
    </div>
    



  </section>

</template>

<script>

  export default  {
    name: 'src-components-formulario',
    props: [],
    mounted () {

    },
    data () {
      return {
        formState : {},
        formData : this.getInicialData(),
        formFinal: this.getInicialData(),
        nombreMinLength : 5,
        nombreMaxLength : 15,
        edadMin: 18,
        edadMax: 120
      }
    },
    methods: {
      getInicialData() {
        return {
          nombre : null,
          edad: null,
          email: null
        }
      },
      enviar() {
        console.log({...this.formData})

        this.formFinal = this.formData
        this.formData = this.getInicialData()
        this.formState._reset()
      }
    },
    computed: {
    
    }
}


</script>

<style>
  .src-components-formulario {

  }
  .jumbotron {
      background-color: rgb(5, 41, 43);
      color: white;
  }

  hr {
    background-color: #bbb;
  }  

  pre {
    color: white;
  }

</style>
