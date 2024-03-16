<template>
    <div>
      <div :style="{ backgroundColor: colorDeFondo }" class="area-cambiable">
        <p>Área de cambio de color</p>
      </div>
  
      <button @click="cambiarColor('white')">Blanco</button>
      <button @click="cambiarColor('black')">Negro</button>
      <button @click="cambiarColor('blue')">Azul</button>
      <button @click="cambiarColor('green')">Green</button>
    </div>
  </template>
  
  <script>
  export default {
    name: 'CambioColorComponent',
    data() {
      return {
        colorDeFondo: '' // Color inicial
      };
    },
    methods: {
      cambiarColor(color) {
        this.colorDeFondo = color;
      }
    }
  }
  </script>
  
  <style scoped>
  .area-cambiable {
    width: 100%;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    margin-bottom: 10px;
  }
  </style>
  

