<template>
  <div class="container">
      <ul v-for="movie in movies" :key="`movie-${movie.id}`">
          <li>Titolo: {{ movie.title }}</li>
          <li>Titolo originale: {{ movie.original_title }}</li>
          <li v-if="movie.original_language === 'it'">Lingua: <img src="@/assets/it.png" alt=""></li>
          <li v-else-if="movie.original_language === 'en'">Lingua: <img src="@/assets/en.png" alt=""></li>
          <li v-else>Lingua: {{ movie.original_language }}</li>
          <li>Voto: {{ movie.vote_average }}</li>
      </ul>
  </div>
</template>

<script>
export default {
    name: 'MoviesList',
    props: {
        movies: Array,
    }
}
</script>

<style scoped lang="scss">
    .container {
        ul {
            li {
                img{
                    height: 1rem;
                }
            }
        }
    }
</style>