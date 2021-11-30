<template>
  <div class="card">
      <ul>
          <li>Titolo: {{ title }}</li>
          <li v-if="poster !== null">
              <img :src="`https://image.tmdb.org/t/p/w500${poster}`" alt="">
            </li>
          <li>Titolo Originale: {{ originalTitle }}</li>
          <li>
              Lingua: 
              <img v-if="isFlag" :src="require(`../assets/${language}.png`)" :alt="language">
              <span v-else>{{ language }}</span>
            </li>
          <li>Voto: {{ vote }}</li>
      </ul>
  </div>
</template>

<script>
export default {
    name: 'Card',
    props: {
        title: String,
        poster: String,
        originalTitle: String,
        language: String,
        vote: Number,
    },
    data() {
        return {
            availablesFlags: ['it', 'en'],
        }
    },
    computed: {
        isFlag() {
            return this.availablesFlags.includes(this.language);
        }
    }
}
</script>

<style scope lang="scss">
    .card {
        img {
            width: 30px;
        }
    }
</style>