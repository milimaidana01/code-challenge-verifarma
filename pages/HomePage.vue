
<template>
  <div style="width: 100vw">
    <HeaderComponent />
    <BackgroundImage />
    <div class="home-page-main">
      <div class="home-page-main-logo">
        <img class="login-form-logo" src="https://i.ibb.co/QF9NmXb/daf1cd39-5d9c-4660-b505-8b6bc63fe776.jpg" />
      </div>
      <div class="home-page-main-text">
        <h1 class="home-page-main-title">The best movies</h1>
        <h2 class="home-page-main-subtitle">Wherever you are.</h2>
      </div>
    </div>

    <div class="home-page-movies">
      <div class="home-page-movies-row">
        <div class="home-page-movie" v-for="movie in movies" :key="movie.imdbID">
          <img @click="goToMovie(movie.imdbID)" class="home-page-movie-img" :src="movie.Poster" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'HomePage',
  mounted () {
    this.callListMovies()
  },
  data () {
    return {
      movies: []
    }
  },
  methods: {
    async callListMovies () {
      try {
        const response = await axios.get('http://www.omdbapi.com/?apikey=6fd1685b&s=harry&page=1')
        this.movies = response.data.Search
        console.log(response)
        console.log(this.movies, 1)
      } catch (error) {
        console.log(error)
      }
    },
    goToMovie (id) {
      this.$router.push('/MoviePage/' + id)
    }
  }
}
</script>

<style>
@import '~/css/components.css';
</style>
