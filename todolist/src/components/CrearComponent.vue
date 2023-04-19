<template>
    <div class="container">
        <h2>Crear una nueva tarea</h2>
        <div class="agregar">   
        </div>
        <div class="formulario">
            <input v-model="titulos" type="text" placeholder="Titulo">
            <textarea v-model="notas" name="" id="" cols="10" rows="5"></textarea>
            <input type="submit" @click="enviar">
        </div>
    </div>

    <div class="sinHacer">
        <div v-for="(tituloNota, index)  in tituloNotas" :key="index" class="notas" >
            <h3>{{  tituloNota.titulo }}</h3>
            <p>{{ tituloNota.nota}}</p>
        </div>
    </div>
   
        
   

</template>
<script setup>
    import { ref } from 'vue';

    const titulos = ref("")
    const notas = ref("")
    const tituloNotas = ref([])

    function enviar(){
        tituloNotas.value.push({
            titulo: titulos.value,
            nota: notas.value,
        })
        titulos.value = ""
        notas.value = ""
    }



</script>
<style scoped>
    .container{
        background-color: aqua;
        display: flex;
        flex-direction: column;
        align-items: center;
        width: 40%;
        margin: 0 auto;
        justify-content: center;
        margin-bottom: 1rem;
    }
    .formulario{
        display: flex;
        flex-direction: column;
        width: 80%;
        margin: 0 auto;
        padding: 1rem;
        gap: 1rem;

    }

    .sinHacer{
        display: flex;
        flex-wrap: wrap;
        gap:1rem;
        width: 70%;
        margin:0 auto
    }

    .notas{
        border: 1px solid black;
        background-color: antiquewhite;
        width: 12rem;
        height: 17rem;
    }

</style>


  