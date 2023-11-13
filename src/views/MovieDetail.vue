<template>
  <div class="movie-detail">
    <h2>{{movie.Title}}</h2>
    <p>{{ movie.Year }}</p>
    <img :src="movie.Poster" alt="Movie Poster" class="featured-img" />
    <p>{{ movie.Plot }}</p>
  </div>
</template>

<script>
import { ref, onBeforeMount } from 'vue';
import { useRoute } from 'vue-router';
import env from '@/env.js';

export default {
  setup () {
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
  padding: 14px;
  display: grid; 
  margin: auto;
  text-align: center;
  max-width: 600px;
  /* background: hotpink; */

  h2 {
    color: #FFF;
    font-size: 28px;
    font-weight: 600;
    margin-bottom: 16px;
  }

  .featured-img {
    display: block;
    max-width: 200px;
    margin: auto;

    text-align: center;
    border: 2px dotted white; 
    background: white;
    padding-bottom: 24px;
  }

  p {
    color: #FFF;
    font-size: 14px;
    line-height: 1.4;
    text-shadow: 0px 2px 2px #000;
    padding-top: 20px;
  
  }
}
</style>