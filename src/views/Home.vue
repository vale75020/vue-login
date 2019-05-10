<template>
  <div class="home">
   <div>
     Movie List | 
     <router-link to="/login">Login</router-link> |
     <router-link to="/create">Movie</router-link>
   </div>
   <hr>

   <div v-for="movie in movies" :key="movie.id">
     <h3>{{movie.title}}</h3>
     <h5>from director: {{movie.director}}</h5>
     <hr>
   </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'home',
  data() {
    return {
      movies: []
    }
  },
  created() {
    axios.get('http://localhost/movies').then((res => {
      if (res.status === 200 && res.data.success) {
        this.movie = res.data.content;

        console.log('this.movies', this.movies)
      }
    }))
  }
  

}
</script>
