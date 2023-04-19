<template>
  <div class="home">
    <CrearComponent @tituloNotas = "tituloNotas"/>
    <SinHacer/>
    <button @click="enseñar">enseñar</button>
    {{ tituloNotas }}
  </div>
</template>

<script>
import { ref } from 'vue';

import CrearComponent from '@/components/CrearComponent.vue'
import SinHacer from '@/components/SinHacer.vue'

export default {
  name: 'HomeView',
  components: {
    CrearComponent,
    SinHacer
  },
  setup() {
    let tituloNotas = ref([]);

    function enseñar() {
      console.log(tituloNotas.value)
    }

    return {
      tituloNotas,
      enseñar
    }
  }
}
</script>
