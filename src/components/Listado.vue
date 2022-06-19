<template>

<b-list-group>
  <h2>Listado</h2>
  <b-list-group-item class="d-flex justify-content-between align-items-center" v-for="gasto in listado" :key="gasto.id">
          <p>{{gasto.nombre}}</p>
      <p>${{gasto.cantidad}}</p>

  </b-list-group-item>
</b-list-group>


</template>

<script>
export default {

    props:{
        listado: {
            type: Array,
            default: [],
        }

    },
        
    data() {
      return {
        presupuesto: 0,
      }
    },



}
</script>

<style>

</style>