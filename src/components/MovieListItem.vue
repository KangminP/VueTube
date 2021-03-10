<template>
  <div class="container">
    <div class="col mb-4">
      <div class="card">
        <img :src="movie.poster_url" class="card-img-top" alt="...">
        <div class="card-body">
          <h5 class="card-title">{{ movie.title }}</h5>
          <button type="button" class="btn btn-primary" data-toggle="modal" :data-target="getMovie">영화 정보 상세보기</button>
        </div>
        <MovieListItemModal :movie="movie"/>
      </div>
    </div>
  </div>
</template>

<script>
import MovieListItemModal from './MovieListItemModal.vue'

export default {
    name: "MovieListItem",
    props: {
      movie: Object,
    },
    components: {
        MovieListItemModal,
    },
    computed: {
      getMovie() {
        return `#movie-${this.movie.id}`
      }
    }
}
</script>

<style>
.card-height {
  height: 100%;
}
</style>