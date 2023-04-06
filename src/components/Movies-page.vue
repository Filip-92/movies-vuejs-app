<template>
  <div class="container p-3">
    <div class="p-3">
      <img :src="logo" alt="cinema" class="col-12">
    </div>
  
    <div v-for="(movie, index) in movies" :key="movie.id">
      <div class="card mb-2" v-bind:style="[chosen[index] ? {'border': '3px double purple'} : {}]">
          <div class="row">
            <span class="col-6">
              <h4 class="mr-2" @click="choiceToggle(index)" v-bind:style="[chosen[index] ? {'color': 'purple'} : {}]">{{changeName(movie.name)}}</h4>
            </span>
            <span class="col-4 col-md-2" v-bind:style="[chosen[index] ? {'color': 'purple'} : {}]">
              <i class="fa fa-clock-o mt-2 ml-3 mr-3"></i>{{movie.duration}}s
            </span>
            <span class="col-2 col-md-4 mt-1">
              <i class="fa fa-arrow-down" v-if="!chosen[index]" @click="choiceToggle(index)"></i>
              <i class="fa fa-arrow-up" v-if="chosen[index]" @click="choiceToggle(index)"></i>
            </span>
          </div>
  
        <div v-if="chosen[index]" class="text-center col-12">
          <MovieDisplay :movie="movie.name" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import MovieDisplay from '@/components/Movie-display.vue'

export default {
  data() { return { 
    logo: require('@/assets/RT_300EssentialMovies_700X250.jpg'),
    movies: [
      {
        id: 0, 
        name: 'Drzewa przy drodze.mp4', 
        duration: '15.08'
      }, 
      {
        id: 1, 
        name: 'Kobieta na peronie.mp4', 
        duration: '32.04'
      }, 
      {
        id: 2, 
        name: 'Wiklina.mp4', 
        duration: '9.80'
      }, 
      {
        id: 3, 
        name: 'Dynia na Halloween.mp4', 
        duration: '17.85'
      }
    ],
    //duration: ['15.08', '32.04', '9.80', '17.85'], 
    chosen: Boolean [Number] = [],
    currentMovie: String, default: null
  }; },
  components: { MovieDisplay },
  methods: {
    choiceToggle(i) {
      for (let n = 0; n < this.movies.length; n++) {
      if (i !== n && this.chosen[n]) {
        this.chosen[n] = false;
      }
    }
    this.chosen[i] = !this.chosen[i]
    this.currentMovie = this.movies[i].name
  },
  changeName(name) {
    if(name.includes("mp4")) {
      return name.replace(".mp4", "")
    } else {
      return null;
    }
  }
}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
a {
  color: #42b983;
}
.container {
  text-align: center;
}

h3 {
  border: 1px solid white;
}

img {
  border-radius: 8px;
}

a {
  color: white !important;
}

h1, p {
font-family: Lato;
}

body {
background-color: #2173D1;
}
.fa-arrow-down:hover, .fa-arrow-up:hover {
  cursor: pointer;
}

.fa-arrow-up {
  color: purple !important;
}
.fa-arrow-up:hover {
  color: red !important;
}
.fa-arrow-down:hover {
  color: rgb(18, 181, 18);
}

video {
  display: none;
}
.card {
  border: 3px double white;
  border-radius: 8px;
  background-color: black;
  color: white !important;
  padding: 10px 0px 5px 0px;
}

.card:hover {
  border: 3px double purple;
  color: purple !important;
}

.card:active {
  border: 3px double purple;
}

.fa-clock-o:hover {
  cursor: default !important;
}

h4:hover {
  cursor: pointer;
}

h4 {
  text-align: right !important;
}

@media screen and (max-width: 1000px) {

  h4 {
    font-size: 18px !important;
    margin-top: 5px !important;
    text-align: center !important;
  }
}

</style>
