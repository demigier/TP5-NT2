<template>
    <header class="navbar">
        <h1> {{ titulo_autor }} </h1>
    </header>
</template>

<script>
    export default ({
        name: 'Header',
        props:{
            titulo:{
                type: String,
                required: true
            },
            autor:{
                type: String,
                required: true
            }
        },
        computed:{
            titulo_autor(){
                return `${this.titulo} by ${this.autor}`
            }
        }
    })
</script>

<style scoped>
    header{
        background-color: rgba(39, 21, 11, 0.822);
        color: white;
    }
</style>