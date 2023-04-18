<template>
  <div class="home">
    <CrearComponent/>
  </div>
</template>

<script>
// @ is an alias to /src
import CrearComponent from '@/components/CrearComponent.vue'

export default {
  name: 'HomeView',
  components: {
    CrearComponent
  }
}
</script>
