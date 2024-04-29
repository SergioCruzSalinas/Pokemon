<script>
import axios from 'axios';

export default {
  data() {
    return {
      nombresPokemon: []
    };
  },
  mounted() {
    const instanciaAxios = axios.create({
      baseURL: 'https://pokeapi.co/api/v2/pokemon/'
    });

    for (let pokemon = 1; pokemon <= 100; pokemon++) {
      instanciaAxios.get(`${pokemon}/`)
        .then(response => {
          this.nombresPokemon.push(response.data.name);
        })
        .catch(error => {
          console.error('Hubo un error al mostrar el nombre:', error);
          // Puedes mostrar un mensaje de error en la interfaz si lo deseas
        });
    }
  }
}
</script>



<template>
  <div>
    <div v-for="nombre in nombresPokemon" :key="nombre">
      <h1>{{ nombre }}</h1>
    </div>
  </div>
</template>