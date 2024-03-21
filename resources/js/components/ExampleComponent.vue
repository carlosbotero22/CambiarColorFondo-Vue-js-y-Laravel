<template>
  <div :style="{ color: textColor, backgroundColor: backgroundColor }" class="color-changer">
    <h2>Cambiador de Color de Fondo</h2>
    <h2>Cambiador de Color de Fondo</h2>
    <h2>Cambiador de Color de Fondo</h2>
    <h2>Cambiador de Color de Fondo</h2>
    <div class="buttons">
      <!-- Botones para cambiar el color de fondo -->
      <button v-for="color in colors" :key="color" :style="{ backgroundColor: color }" @click="changeColor(color)">
        Cambiar
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ColorChanger',
  data() {
    return {
      backgroundColor: '#FFFFFF', // Color de fondo inicial
      textColor: '#000000', // Color de texto inicial
      colors: ['#FFFFFF', '#000000', '#FF0000', '#00FF00', '#0000FF', '#FFFF00'], // Lista de colores para los botones
    };
  },
  methods: {
    changeColor(color) {
      this.backgroundColor = color;
      this.updateTextColor(color);
    },
    updateTextColor(color) {
      // Algoritmo para determinar si el color de fondo es claro u oscuro
      const colorValue = color.substring(1); // Elimina el #
      const rgb = parseInt(colorValue, 16); // Convierte a un número entero
      const red = (rgb >> 16) & 0xff;
      const green = (rgb >> 8) & 0xff;
      const blue = (rgb >> 0) & 0xff;
      const brightness = (red * 299 + green * 587 + blue * 114) / 1000;
      this.textColor = brightness > 155 ? '#000000' : '#FFFFFF';
    },
  },
};
</script>

<style>
.color-changer {
  width: 100%;
  height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.buttons button {
  margin: 5px;
  padding: 10px;
  border: none;
  cursor: pointer;
  color: #fff;
}

.buttons button:hover {
  opacity: 0.9;
}
</style>
