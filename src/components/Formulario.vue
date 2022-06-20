<template>
  <div>
    <h2 class="text-center">Ingresa tus gastos</h2>
    <b-form @submit="onSubmit" v-if="show">


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

        <div class="d-flex justify-content-center my-4">
          <b-button type="submit" variant="primary">Agregar</b-button>
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
        if (isNaN(this.gasto.cantidad)) {
            alert('Cantidad Inválida')
            return;
        }
        this.$emit('gasto_creado', {...this.gasto})
        //enviando datos 
      },
    }
  }
</script>