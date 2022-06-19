<template>
<b-container class="mt-5">
  <Pregunta 
    v-if="mostrarPregunta"
    v-on:recibir_presupuesto="recibirPresupuesto" 
    
    />
  <Formulario 
    v-if="mostrarFormulario"
    v-on:gasto_creado="ingresarNuevoGasto" 
  />

  <Listado
    v-if="mostrarListado"
    v-bind:listado="listadoGastos"
  />
  <div v-if="presupuesto != 0" class="informacion">
    <h4 class="bg-primary text-center p-2">presupuesto: {{presupuesto}}</h4>
    <h4 class="bg-danger text-center p-2">RESTANTE: {{restante}}</h4>
  </div>
</b-container>
</template>

<script>
import Formulario from './Formulario.vue'
import Listado from './Listado.vue'
import Pregunta from './Pregunta.vue'

export default {

    components: {
        Pregunta,
        Formulario,
        Listado  
    },
    data(){
        return{
            mostrarPregunta: true,
            mostrarFormulario: false,
            listadoGastos: [],
            mostrarListado: false,
            presupuesto: 0,
            gastado: 0,
            restante: 0
        }
    },
    methods: {
        recibirPresupuesto(presupuesto){

            this.mostrarPregunta = presupuesto != 0;
            this.presupuesto = presupuesto;
            this.mostrarFormulario = true;
        },
        ingresarNuevoGasto(gasto){
            this.listadoGastos.push(gasto);
            this.gastado += gasto.cantidad;
            this.restante = this.presupuesto - this.gastado;
            this.mostrarListado= true;
            console.log(this.listadoGastos)
        }
    }

}
</script>

<style>

</style>