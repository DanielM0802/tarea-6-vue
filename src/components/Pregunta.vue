<template>
          <div>
            <h2 class="text-center">Coloca tu presupuesto</h2>
            <form
                @submit.prevent="guardarPresupuesto"
            >

                <b-card>
                    <b-form-input v-model.number="presupuesto" placeholder="Ingresa tu presupuesto"></b-form-input>
                </b-card>
                <div class="d-flex justify-content-center mt-2">
                    <b-button type="submit" variant="outline-primary">Definir Presupuesto</b-button>
                </div>
            </form>
        </div>
</template>

<script>
export default {

    data(){
        return{
            presupuesto: 0,
            mostrarPregunta: true
        }
    },
    methods: {
        guardarPresupuesto(){
            if (this.presupuesto < 1 || isNaN(this.presupuesto)) {
                alert('Presupuesto Inválido')
                return;
            }
            this.mostrarPregunta = false
            this.$emit('recibir_presupuesto', this.presupuesto)
            this.$emit('presupuesto', this.presupuesto)
        },
    },
}
</script>

<style>

</style>