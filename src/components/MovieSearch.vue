<template>
    <div class="contenido">
      <h1 class="title is-3 has-text-centered">Lista de Películas Populares</h1>
      
      <form @submit.prevent="buscarPeliculas" class="mb-4">
      <div class="field has-addons has-addons-centered">
        <div class="control">
          <input v-model="busqueda" class="input" type="text" placeholder="Buscar película">
        </div>
        <div class="control">
          <button type="submit" class="button is-info">
            Buscar
          </button>
        </div>
      </div>
    </form>

      <div class="columns is-multiline">
        <div v-for="movie in movies" :key="movie.id" class="column is-one-third">
          <div class="card">
            <div class="card-image">
              <figure class="image is-4by3">
                <img :src="'https://image.tmdb.org/t/p/w500/' + movie.poster_path" alt="Poster de la película">
              </figure>
            </div>
            <div class="card-content">
              <p class="title is-5">{{ movie.title }}</p>
              
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  import axios from 'axios';

export default {
  data() {
    return {
      movies: [],
      busqueda: '', // Nuevo dato para almacenar la entrada del usuario
    };
  },
  methods: {
    buscarPeliculas() {
      // Realiza la búsqueda solo si hay texto en el campo de búsqueda
      if (this.busqueda.trim() !== '') {
        // Reemplaza 'TU_CLAVE_DE_API' con la clave que obtuviste
        const apiKey = '5bdcb9ae2a5dc30a6d1007c3e0cc33a7';
        const apiUrl = 'https://api.themoviedb.org/3'; // Reemplaza con la URL de la API

        axios.get(`${apiUrl}/search/movie?api_key=${apiKey}&query=${this.busqueda}`)
          .then(response => {
            this.movies = response.data.results;
          })
          .catch(error => {
            console.error('Error al buscar películas:', error);
          });
      } else {
        // Si el campo de búsqueda está vacío, puedes manejarlo de acuerdo a tus necesidades
        console.log('Ingresa un título de película para buscar.');
      }
    },
  },
}
  </script>
<style>
     .contenido div:hover{
        background-color: aliceblue;
        cursor:pointer
    }
</style>
  