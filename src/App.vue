<template>
	<div id="app">
      <Header @performSearch="searchMoviesAndTV"/>
      <MoviesList :movies="moviesList" :tvs="TVList"/>
	</div>
</template>

<script>
import axios from 'axios';
import Header from '@/components/Header.vue';
import MoviesList from '@/components/MoviesList.vue';

export default {
  name: 'App',
  components: {
	Header,
	MoviesList,
  },
  data() {
    return {
      moviesList: null,
      TVList: null,
      searchText: '',
    }
  },
  methods: {
    searchMoviesAndTV(text) {
      if(text !== '') {
        this.searchText = text;
        axios.get('https://api.themoviedb.org/3/search/movie' , {
          params: {
            api_key: '4dfb8a20463f35995cde083233294355',
            query: this.searchText,
            language: 'it-IT',
          }
        })
        .then(response => {
          console.log(response.data.results);
          this.moviesList = response.data.results;
        })
        .catch(err => console.log(err));

        axios.get('https://api.themoviedb.org/3/search/tv' , {
          params: {
            api_key: '4dfb8a20463f35995cde083233294355',
            query: this.searchText,
            language: 'it-IT',
          }
        })
        .then(response => {
          console.log(response.data.results);
          this.TVList = response.data.results;
        })
        .catch(err => console.log(err));
      }
    },
  },
}
</script>

<style lang="scss">
  body {
    height: 100vh;
    background: red !important;
  }
</style>
