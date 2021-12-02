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
      datas: ''
    }
  },
  methods: {
    searchMoviesAndTV(text, info) {
      if(text !== '') {
        this.searchText = text;
        this.datas = info;
        if(this.datas === 'all') {
          console.log('ciao');
          this.searchMovie(this.searchText);
          this.searchTV(this.searchText);
        }
        else if(this.datas === 'movies') {
          this.searchMovie(this.searchText);
          this.TVList = null;
        }
        else {
          this.searchTV(this.searchText);
          this.moviesList = null;
        }
      }
    },
    searchMovie(searchText) {
      axios.get('https://api.themoviedb.org/3/search/movie' , {
          params: {
            api_key: '4dfb8a20463f35995cde083233294355',
            query: searchText,
            language: 'it-IT',
          }
        })
        .then(response => {
          console.log(response.data.results);
          this.moviesList = response.data.results;
        })
        .catch(err => console.log(err));
    },
    searchTV(searchText) {
      axios.get('https://api.themoviedb.org/3/search/tv' , {
          params: {
            api_key: '4dfb8a20463f35995cde083233294355',
            query: searchText,
            language: 'it-IT',
          }
        })
        .then(response => {
          console.log(response.data.results);
          this.TVList = response.data.results;
        })
        .catch(err => console.log(err));
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
