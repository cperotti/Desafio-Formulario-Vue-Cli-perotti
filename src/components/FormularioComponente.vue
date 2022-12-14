<template>
  <div class="d-flex flex-column justify-content-center align-items-center">
    <div v-if="message" class="alert alert-success">
      {{message}}
    </div>
    <div class="card border-warning mb-3 card-container">
  <div class="card-body">
    <form id="formulario" @submit.prevent="validaciones">
        <div class="row">
            <h5>Comida</h5>
            <p v-if="errores.comida" class="card-text"><small class="text-danger">{{errores.comida}}</small></p>
              <div class="col" v-for="(comida,index) in comidas" :key="index">
                <input v-model="comidaSeleccionada" class="form-check-input" type="checkbox" :value="`${comida.name.toLowerCase()}`" :id="`${comida.name.toLowerCase()}`">
                <label class="form-check-label" :for="`${comida.name.toLowerCase()}`">
                  {{comida.name}}
                </label>
              </div>
          </div>
          <br />
          <div class="row">
            <h5>Bebida</h5>
            <p v-if="errores.bebida" class="card-text"><small class="text-danger">{{errores.bebida}}</small></p>
            <div class="col" v-for="(bebida, index) in bebidas" :key="index">
              <input v-model="bebidaSeleccionada" :value="`${bebida.name.toLowerCase()}`" type="radio" :name="`check${bebida.name.toLowerCase()}`" class="form-check-input">
              <label :for="`check${bebida.name.toLowerCase()}`">{{bebida.name}}</label>
            </div>
        </div>
        <br />
        <div class="row">
            <div class="col col-12">
                <label for="cantidad" class="form-label text-start">Cantidad</label>
                <input v-model="cantidad" min="1" type="number" class="form-control" id="cantidad" >
            </div>
        </div>
        <br />
        <div class="row">
            <div  class="col col-12">
                <label for="email" class="form-label text-start">Email</label>
                <input v-model="email" type="email" class="form-control" id="email">
                <p v-if="errores.email" class="card-text"><small class="text-danger">{{errores.email}}</small></p>
            </div>
        </div>
        <br />
        <div class="row">
            <div class="col col-12">
                <label for="direccion" class="form-label text-start">Direccion</label>
                <input v-model="direccion" type="text" class="form-control" id="direccion">
                <p v-if="errores.direccion" class="card-text"><small class="text-danger">{{errores.direccion}}</small></p>
            </div>
        </div>
        <br />
        <div>
          <label for="comentarios" class="form-label text-start">Comentarios</label>
          <textarea v-model="comentarios" class="form-control" id="comentarios" rows="3"></textarea>
        </div>
        <br />
        <div class="d-grid gap-2">
            <button id="buton" @click="enviarDatosTabla" type="submit" class="btn btn-primary">Enviar</button>
        </div>
    </form>
    </div>
    </div>
  </div>
</template>

<script>
export default {
    name:'FormularioComponente',
    data() {
        return {
            errores:{
                comida:'',
                bebida:'',
                direccion:'',
                email:''
            },
            message:'',
            comidaSeleccionada:[],
            comidas:[
                {
                    name:'Hamburguesas'
                },
                {
                    name:'Pizza'
                },
                {
                    name:'Sandwich'
                },
                {
                    name:'Papas fritas'
                }
            ],
            bebidaSeleccionada:'',
            bebidas:[
                {
                    name:'Coca-cola'
                },
                {
                    name:'Seven-up'
                },
                {
                    name:'Agua'
                },
                {
                    name:'Jugo'
                }
            ],
            comentarios:'',
            direccion:'',
            email:'',
            cantidad:1,
        }
    },
    methods:{
        enviarDatosTabla(){
            if(this.direccion && this.comidaSeleccionada.length > 0 && this.bebidaSeleccionada && this.email){
                this.errores= {
                comida:'',
                bebida:'',
                direccion:'',
                email:'',
                }
                this.$emit("enviarDatosTabla", {comida:this.comidaSeleccionada, bebida:this.bebidaSeleccionada, cantidad: this.cantidad, email: this.email,  direccion: this.direccion, comenentarios: this.comentarios})
                this.message= 'El pedido se envió con éxito!!'
            }
        },
        validaciones(){

            if(this.direccion && this.comidaSeleccionada.length > 0 && this.bebidaSeleccionada && this.email){
                setTimeout(() => {
                document.getElementById('formulario').reset()
                Object.assign(this.$data, this.$options.data())
                }, 3000);
                return true
            }

            if(this.comidaSeleccionada.length === 0){
                this.errores = {...this.errores, comida:'Debes elegir almenos una comida'} 
            }else{
                this.errores = {...this.errores, comida:''}
            }
            if(!this.bebidaSeleccionada){
                this.errores = {...this.errores, bebida:'Debes seleccionar una bebida'} 
            }else{
                this.errores = {...this.errores, bebida:''}
            }
            if(!this.direccion){
                this.errores = {...this.errores, direccion:'Debes ingresar una direccion'} 
            }else{
                this.errores = {...this.errores, direccion:''}
            }
            if(!this.email){
                this.errores = {...this.errores, email:'Debes ingresar un email'} 
            }else{
                this.errores = {...this.errores, email:''}
            }
                }
    }
}
</script>

<style scope>
.card-container{
    width: 700px;
}
</style>