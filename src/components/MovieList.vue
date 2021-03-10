<template>
  <div class="container mt-5">
    <div class="row row-cols-1 row-cols-md-4">
      <MovieListItem v-for="movie in movies" :key="movie.id" :movie="movie"/> 
    </div>
      <!-- <ul class="col">
        <li v-for="movie in movies" :key="movie.id">
          {{ movie.title }}
          <MovieListItem />
        </li>
      </ul> -->
  </div>
</template>

<script>
import MovieListItem from './MovieListItem.vue'

export default {
  name: "MovieList",
  props: {
    movies: Array,
  },
  components: {
    MovieListItem,
  }
}
</script>

<style>

</style>