<template>
  <div>
    <b-form @submit="onSubmit" @reset="onReset" v-if="show">


      <b-form-group id="input-group-1" label="Nombre gasto:" label-for="input-1">
        <b-form-input
          id="input-1"
          v-model="gasto.nombre"
          placeholder="Ingresa un nombe Ej. Transporte"
          required
        ></b-form-input>
      </b-form-group>
      <b-form-group id="input-group-2" label="Cantidad gasto:" label-for="input-2">
        <b-form-input
          id="input-2"
          v-model.number="gasto.cantidad"
          placeholder="Ingresa gasto Ej. 7000"
          required
        ></b-form-input>
      </b-form-group>

        <div class="d-flex justify-content-evenly my-4">
          <b-button type="submit" variant="primary">Submit</b-button>
          <b-button type="reset" variant="danger">Reset</b-button>
      </div>
    </b-form>

  </div>
</template>

<script>
  export default {
    data() {
      return {
        gasto: {
          nombre: '',
          cantidad: 0
        },
        show: true
      }
    },
    methods: {
      onSubmit(event) {
        event.preventDefault()
        this.$emit('gasto_creado', this.gasto)
        console.log(this.gasto)

        //enviando datos 

      },
      onReset(event) {
        event.preventDefault()
        // Reset our form values
        this.gasto.nombre = ''
        this.gasto.cantidad = 0
        // Trick to reset/clear native browser form validation state
        this.show = false
        this.$nextTick(() => {
          this.show = true
        })
      },
    }
  }
</script>