<template>
    <div>
      <h1 class="title is-3 has-text-centered">{{ movie.title }}</h1>
      <div class="columns">
        <div class="column is-one-third">
          <figure class="image is-4by3">
            <img :src="'https://image.tmdb.org/t/p/w500/' + movie.poster_path" :alt="movie.title + ' Poster'">
          </figure>
        </div>
        <div class="column">
          <p><strong>Fecha de lanzamiento:</strong> {{ movie.release_date }}</p>
          <p><strong>Calificación:</strong> {{ movie.vote_average }}</p>
          <p><strong>Descripción:</strong> {{ movie.overview }}</p>
        </div>
      </div>
      <router-link to="/" class="button is-info">Volver a la lista</router-link>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      movie: Object,
    },
  };
  </script>
  
  <style scoped>
  /* Estilos específicos del componente MovieDetail */
  </style>
  