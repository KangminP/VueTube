<template>
  <div class="container mt-4">
    <h1 class="mt-5"><img src="../assets/camera.png" width="60px"> 나만의 무비 컬렉션</h1>
    <button v-if="!movies" type="button" class="btn btn-primary mt-5" @click="getPost">영화가져오기</button>
    <br>
    <img src="../assets/people.jpg" v-if="!movies" class="mt-5">
    <MovieList :movies="movies" />
  </div>
</template>

<script>
import axios from 'axios'
import _ from 'lodash'

import MovieList from '../components/MovieList.vue'

export default {
  name: 'MovieView',
  components: {
    MovieList,
  },
  data() {
    return {
      movies: null,
    }
  },
  methods: {
    getPost() {
      axios.get("http://www.json-generator.com/api/json/get/ceNyuXZmwi?indent=2")
      .then(res => {
        this.movies = res.data
        this.movies.forEach(movie => {
            movie.title = _.unescape(movie.title)
            movie.overview = _.unescape(movie.overview)
        })
      })
      .catch(err => {
        console.error(err)
      })
    }
  }
}
</script>
