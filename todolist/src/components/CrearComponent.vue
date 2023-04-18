<template>
    <div class="container">
        <h2>Crear una nueva tarea</h2>
        <div class="agregar">
            <button>+</button>
        </div>
    </div>
    <div class="overlay">
        <div class="formulario">
            <h2>hola</h2>
            <input type="text" placeholder="Nombre">

            <input type="text" placeholder="Nota">
        </div>
    </div>

</template>
<script>


</script>
<style scoped>
    .container{
        background-color: aqua;
        display: flex;
        align-items: center;
        width: 60%;
        margin: 0 auto;
        justify-content: center;
        gap: 2rem;
    }
    .formulario{
        display: flex;
        flex-direction: column;
        width: 20%;
        margin: 0 auto;
        background-color: aquamarine;
        padding: 1rem;

    }

</style>


  