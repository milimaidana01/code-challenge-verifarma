
<template>
  <div>
    <HeaderComponent />

    <BackgroundImage />
    <div class="movie-page-main">
      <div class="movie-page-left">
        <img :src="movie.Poster" alt="">
      </div>
      <div class="movie-page-right">
        <div class="movie-page-title">
          {{ movie.Title }}
        </div>
        <div class="movie-page-subtitle">
          {{ movie.Plot }}
        </div>

        <button class="movie-page-btn">Play</button>

        <div class="movie-page-actors">
          {{ movie.Actors }}
        </div>
        <div class="movie-page-director">
          {{ movie.Director }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'MoviePage',
  mounted () {
    this.callGetMovieData()
  },
  data () {
    return {
      movie: {}
    }
  },
  methods: {
    async callGetMovieData () {
      try {
        const response = await axios.get('http://www.omdbapi.com/?apikey=6fd1685b&i=' + this.$route.params.id)
        this.movie = response.data
      } catch (error) {
        console.log(error)
      }
    }
  }
}
</script>

<style>
  @import '~/css/components.css';
</style>
