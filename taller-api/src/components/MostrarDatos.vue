<template>
  <div>
    <h2>Datos Poblacion</h2>
    <ul v-if="data.length">
      <li v-for="(item, index) in data" :key="index">
        {{ item.country }}: {{ item.population }}
      </li>
    </ul>
    <p v-else>No hay datos disponibles.</p>
  </div>
</template>

<script>
export default {
  props: {
    data: {
      type: Array,
      required: true
    }
  }
};
</script>

<style scoped>
h2 {
  font-size: 20px;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  margin: 5px 0;
}
</style>

