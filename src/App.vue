<template>
	<div id="app">
		<Header @performSearch="searchMovies"/>
		<MoviesList :movies="moviesList"/>
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
      searchText: '',
    }
  },
  methods: {
    searchMovies(text) {
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
    }
  },
}
</script>

<style lang="scss">

</style>
