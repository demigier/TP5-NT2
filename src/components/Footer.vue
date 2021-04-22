<template>
    <footer>
        <h1> {{ titulo_autor }} </h1>
    </footer>
</template>

<script>
export default {
    name: 'Footer',
    props:{
        titulo:{
            type: String,
            required: true
        },
        autor:{
            type: String,
            required: true
        },
    },
    computed:{
        titulo_autor(){
            return `${this.titulo} by ${this.autor}`
        }
    },
    methods:{

    }
}
</script>

<style>
    footer{
        background-color: rgba(39, 21, 11, 0.822);
        color: white;
    }
</style>