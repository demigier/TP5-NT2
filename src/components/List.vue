<template>
    <div>
        <input v-model="descripcion" v-bind:placeholder="phdesc">
        <input v-model="precio" v-bind:placeholder="phprecio">
        <button @click="agregar" v-if='!modificando' class="btn btn-info"> Agregar </button>
        <button @click="modificar" v-if='modificando' class="btn btn-warning"> Modificar </button>

        <ul>
            <li v-for="producto in productos" v-bind:key=producto.id>
                <p> - {{ producto.descripcion }} ${{ producto.precio }} </p>
                <div class="botones">
                    <button @click="cambiarModificar(producto.id)" class="btn btn-warning"> Modificar </button>
                    <button @click="eliminar(producto.id)" class="btn btn-danger"> Eliminar </button>
                </div>
            </li>
        </ul>
    </div>    
</template>

<script>
export default {
    name: 'List',
    data(){
        return{
            productos:[
                {
                    id: 0,
                    descripcion: 'Coca Cola',
                    precio: 80
                },
                {
                    id: 1,
                    descripcion: 'PolyStation',
                    precio: 50
                }
            ],
            id: '',
            descripcion: '',
            precio: '',
            phid: 'Ingrese el id',
            phdesc: 'Ingrese la descripcion',
            phprecio: 'Ingrese el precio',
            modificando: false,
            button: 'Agregar'
        }
    },
    methods:{
        cambiarModificar(_id){
            this.modificando = true;

            const pos = this.productos.findIndex(p => p.id == _id);
            if(pos > -1){
                this.id = pos;
                this.descripcion = this.productos[pos].descripcion;
                this.precio = this.productos[pos].precio;
                this.button = 'Modificar';
            }else{
                console.error('ID inexistente');
            }
        },
        modificar(){
            if(this.descripcion != '' && this.precio != '' && this.id.toString() != ''){
                this.productos[this.id] = {
                    id: this.id,
                    descripcion: this.descripcion,
                    precio: this.precio
                }
            }else{
                console.error('No deje campos vacios');
            }

            this.vaciar();
            this.modificando = false;
        },
        eliminar(_id){
            if(this.productos.findIndex(p => p.id == _id) != null){
                this.productos.pop(_id);
            }else{
                console.error('ID inexistente');
            }
        },
        agregar(){
            if(this.descripcion != '' && this.precio != ''){
                this.productos.push({
                    id: this.productos.length,
                    descripcion: this.descripcion,
                    precio: this.precio
                })
                this.vaciar();
            }else{
                console.error('No deje campos vacios');
            }
        },
        vaciar(){
            this.precio = '';
            this.descripcion = '';
            this.id = '';
        }
    }
}
</script>

<style>
    li{
        list-style: none;
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
    /* *{
        margin: 10px;
    } */
    .botones{
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
</style>