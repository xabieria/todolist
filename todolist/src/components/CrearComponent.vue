<template>
    <div class="container">
        <h2>Crear una nueva tarea</h2>
        <div class="agregar">   
        </div>
        <div class="formulario">
            <input v-model="titulos" type="text" placeholder="Titulo">
            <textarea v-model="notas" name="" id="" cols="10" rows="5"></textarea>
            <input type="submit" @click="upNotes">
        </div>
    </div>

    <div class="sinHacer">
        <div v-for="datoJson in datosJson" :key="datoJson.id" class="notas">
            <button @click="editNotes(datoJson.id)">Editar</button>
            <h3>{{  datoJson.titulo }}</h3>
            <p>{{ datoJson.nota}}</p>
            <button @click="deleteNotes(datoJson.id)">Borrar</button>
        </div>
    </div>

    <div class="editar" v-show="mostrar">
        <input type="text" v-model="editarTitulo" placeholder="titulo nuevo">
        <input type="text" v-model="editarNota" placeholder="Nota nuevo">
        <button @click="saveEditNotes">Editar</button>
    </div>
   
        
   

</template>
<script setup>
    import { ref } from 'vue';
    import axios from 'axios'

    const titulos = ref("")
    const notas = ref("")
    const datosJson = ref("")
    let mostrar = ref(false)
    const idTask = ref("")
    const editarTitulo = ref("")
    const editarNota = ref("")

    const getNotes = async () => {
        try {
            const { data } = await axios.get("http://localhost:3000/nota")
            datosJson.value = data;
            console.log(data)
        } catch (error) {
            console.log("error")
        }
    }  
    getNotes();

    const upNotes = ()=> {
        axios.post("http://localhost:3000/nota",{
            "titulo" : titulos.value,
            "nota" : notas.value
        })
        location.reload()
    }

    function deleteNotes(id) {
        axios.delete(`http://localhost:3000/nota/${id}`)
        location.reload()
    }

    function editNotes(id){
        mostrar.value = true
        idTask.value =  id
        console.log(idTask.value)
    }

    function saveEditNotes(){
        try {
            axios.put(`http://localhost:3000/nota/${idTask.value}`,{
                "titulo" : editarTitulo.value,
                "nota" : editarNota.value
            })
        } catch (error) {
            console.log("error")
        }
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
        height: auto;
        padding-bottom: 1rem;
        padding-top: 1rem;
    }

</style>


  