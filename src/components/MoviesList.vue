<template>
  <div class="container">
      <div v-for="movie in movies" :key="`movie-${movie.id}`">
          <Card 
            :title="movie.title"
            :poster="movie.poster_path"
            :originalTitle="movie.title"
            :language="movie.original_language"
            :vote=" movie.vote_average"
          />
      </div>
      <div v-for="tv in tvs" :key="`tv-${tv.id}`">
          <Card 
            :title="tv.name"
            :poster="tv.poster_path"
            :originalTitle="tv.original_name"
            :language="tv.original_language"
            :vote=" tv.vote_average"
          />
      </div>
  </div>
</template>

<script>
import Card from '@/components/Card.vue';

export default {
    name: 'MoviesList',
    components: {
        Card,
    },
    props: {
        movies: Array,
        tvs: Array,
    }
}
</script>

<style scoped lang="scss">

</style>