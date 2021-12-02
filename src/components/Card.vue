<template>
  <div class="card">
      <img v-if="poster !== null" :src="`https://image.tmdb.org/t/p/w342${poster}`" alt="">
      <div class="overlay">
        <ul>
            <li>Titolo: {{ title }}</li>
            <li>Titolo Originale: {{ originalTitle }}</li>
            <!-- <li>
                Lingua: 
                <img v-if="isFlag" :src="require(`../assets/${language}.png`)" :alt="language">
                <span v-else>{{ language }}</span>
                </li> -->
            <li>Voto: <i v-for="n in stars(vote)" :key="`fullStar-${n}`" class="fas fa-star"></i><i v-for="n in 5-stars(vote)" :key="`emptyStar-${n}`" class="far fa-star"></i>  </li>
        </ul>
      </div>
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
    },
    methods: {
        stars(number) {
            if(Math.ceil(number)/2) {
                return parseInt(Math.ceil(number)/2);
            }
            return 0;
        }
    }
}

</script>

<style scope lang="scss">
    .card {
        position: relative;
        margin-bottom: 10px ;

        .overlay {
            position: absolute;
            width: 100%;
            height: 100%;
            opacity: 0;
            background: rgba($color: #000000, $alpha: .8);
            transition: opacity .5s;
            padding: 1rem;
        }
        ul {
            list-style: none;
            color: #fff;
        }

        &:hover {
            .overlay {
                 opacity: 1;

            }
        }
    }
</style>