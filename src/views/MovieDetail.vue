<template>
    <div class="movie-data">Detail {{ $route.params.id }}</div>
    <h2>{{ movie.Title }}</h2>
    <p>{{ movie.Year }}</p>
    <img :src="movie.Poster" alt="Movie Poster" class="featured-img" />
    <p>{{ movie.Plot }}</p>
</template>

<script> 
import { ref, onBeforeMount } from 'vue'; 
import { useRoute } from 'vue-router'; 
import env from '@env.js';

export default {
    setup() {
        const movie = ref({});
        const route = useRoute();

        onBeforeMount(() => {
          fetch(`http://www.omdbapi.com/?apikey=${env.apikey}&i=${route.params.id}&plot=full`)
            .then(response => response.json())
            .then(data => {
          movie.value = data;
        });
    });
    

    return {
        movie
    }
  }
}
</script>

<style lang="scss">

.movie-detail {
  padding: 16px;

  h2 {
    color: ghostwhite;
    font-size: 24px;
    font-weight: 600;
    margin-bottom: 14px;
  }

  .featured-img {
    display: block;
    max-width: 200px;
    margin-bottom: 16px;
  }

  p {
    color: ghostwhite;
    font-size: 18px;
    line-height: 1.4;
  }
}

</style>
