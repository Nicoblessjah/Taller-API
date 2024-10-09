<template>
  <div class="container">
    <h1>Consumir APIs</h1>
    <BotonAPI
        label="Obtener Población de Países"
        endpoint="https://countriesnow.space/api/v0.1/countries/population"
        @data-fetched="updateData"
    />
    <BotonAPI
        label="Obtener Recomendaciones de Anime"
        endpoint="https://api.jikan.moe/v4/recommendations/anime"
        @data-fetched="updateData"
    />
    <BotonAPI
        label="Obtener Anime Aleatorio"
        endpoint="https://api.jikan.moe/v4/random/anime"
        @data-fetched="updateData"
    />
    <BotonAPI
        label="Obtener Manga Aleatorio"
        endpoint="https://api.jikan.moe/v4/random/manga"
        @data-fetched="updateData"
    />
    <MostrarDatos :data="apiData" />
  </div>
</template>

<script>
import BotonAPI from '@/components/BotonAPI.vue';
import MostrarDatos from '@/components/MostrarDatos.vue';

export default {
  components: {
    BotonAPI,
    MostrarDatos
  },
  data() {
    return {
      apiData: [] // Cambia de objeto a un arreglo
    };
  },
  methods: {
    updateData(data) {
      console.log('Actualizando datos:', data); // Log para depuración
      if (data.error === false) {
        // Asegúrate de asignar solo los datos de población
        this.apiData = data.data; // Cambia esto si los datos vienen en un formato diferente
      } else {
        this.apiData = []; // Limpiar datos si hay un error
        alert(data.msg); // Muestra un mensaje de error si existe
      }
    }
  }
};
</script>

<style scoped>
.container {
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
}

h1 {
  font-family: Arial, sans-serif;
}
</style>
