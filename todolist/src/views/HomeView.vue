<template>
  <div class="home">
    <CrearComponent @tituloNotas = "tituloNotas"/>
    <SinHacer/>
    {{tituloNotas}}
  </div>
</template>

<script>
// @ is an alias to /src
import CrearComponent from '@/components/CrearComponent.vue'
import SinHacer from '@/components/SinHacer.vue'

export default {
  name: 'HomeView',
  components: {
    CrearComponent,
    SinHacer
  }
}
</script>
