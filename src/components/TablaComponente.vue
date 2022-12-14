<template>
  <div>
    <h4>Tabla de pedidos</h4>
    <table class="table table-bordered table-light">
            <thead>
                <tr>
                    <th v-for='(columna, key) in columnas' :key='key'>{{columna.name}}</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(data,index) in dataTabla" :key="index">
                    <td>{{data.comida.join(', ')}}</td>
                    <td>{{data.bebida}}</td>
                    <td>{{data.cantidad}}</td>
                    <td>{{data.email}}</td>
                    <td>{{data.direccion}}</td>
                    <td>{{data.comenentarios}}</td>
                </tr>
            </tbody>
        </table>
  </div>
</template>

<script>
export default {
    name:'TablaComponente',
    props:{
        dataTabla: Array,
    },
    data() {
        return {
            columnas:[
                {
                    name:'Comida'
                },
                {
                    name:'Bebida'
                },
                {
                    name:'Cantidad'
                },
                {
                    name:'Email'
                },
                {
                    name:'Direccion'
                },
                {
                    name:'Comentarios'
                }
            ]
        }
    },
}
</script>

<style>

</style>