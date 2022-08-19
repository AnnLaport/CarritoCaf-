<template>
    <div>
        <input type="text"  class="form-control my-3" 
        placeholder="inserta sabor de café" 
        v-on:keyup.enter="agregarCafe"
        v-model="productocafe" />
        <button class="btn btn-warning" @click="agregarCafe">Insertar</button>
        <div class="my-2" v-for="(item,index) in pedidos" :key="item">
            <div :class="['alert', item.status ? 'alert-success' : 'alert-info']" role="alert">
                <div class="d-flex justify-content-between align-items-center">
                    <div>
                        {{index}} - {{item.name}} - {{item.status}}
                    </div>
                    <div>
                        <button class="btn btn-success" @click="editartarea(index)">OK</button>
                        <button class="btn btn-danger" @click="eliminartarea(index)">X</button>
                    </div>
                </div> 
            </div>
        </div>
        
    </div>
</template>

<script>
    export default {
        name: 'ProductoComp',
        data(){
            return{
                pedidos: [],
                productocafe:''
            }
        },
        methods: {
            agregarCafe(){
                /* console.log(this.productocafe) */
                this.pedidos.push({
                    name: this.productocafe,
                    status: false
                })
                
                this.productocafe=''
                localStorage.setItem('pedidosCafe', JSON.stringify(this.pedidos))
            },
            editartarea(index){
                this.pedidos[index].status=true
                localStorage.setItem('pedidosCafe', JSON.stringify(this.pedidos))
            },
            eliminartarea(index){
                this.pedidos.splice(index, 1) 
                localStorage.setItem('pedidosCafe', JSON.stringify(this.pedidos))
            }
        },
        created: function(){
            let LSdata= JSON.parse(localStorage.getItem('pedidosCafe'))
        
            if(LSdata===null){
                this.pedidos=[]
            }else{
                this.pedidos=LSdata
            }
        }
    }
</script>