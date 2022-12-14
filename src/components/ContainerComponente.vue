<template>
  <div class="d-grid gap-3">
    <h1>Has tu pedido</h1>
    <formulario-componente @enviarDatosTabla="dataTabla.push($event)" />
    <tabla-componente :dataTabla="dataTabla"/>
  </div>
</template>

<script>
import FormularioComponente from './FormularioComponente.vue'
import TablaComponente from './TablaComponente.vue'
export default {
  components: { FormularioComponente, TablaComponente },
    name:'ContainerComponente',
    data() {
        return {
            dataTabla:[]
        }
    },
}
</script>

<style>

</style>