<template>
  <button @click="fetchData">{{ label }}</button>
</template>

<script>
export default {
  props: {
    label: {
      type: String,
      required: true
    },
    endpoint: {
      type: String,
      required: true
    }
  },
  methods: {
    async fetchData() {
      try {
        const response = await fetch(this.endpoint);
        const data = await response.json();
        this.$emit('data-fetched', data); // Emitir los datos al componente padre
        this.$emit('datos recibidos', data); // Emitir los datos al componente padre
      } catch (error) {
        console.error('Error al obtener los datos:', error);
      }
    }
  }
};
</script>

<style scoped>
button {
  margin: 5px;
  padding: 10px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}
button:hover {
  background-color: #0056b3;
}
</style>
