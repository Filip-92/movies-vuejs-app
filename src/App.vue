<template>
  <div class="custom-navbar">
      <div class="custom-navbar-brand">
        <span style="float: left !important;">
          <a href="#" class="ml-2">
            <i href="/hello" class="fa fa-film mr-2"></i><span>Filmy</span>
          </a>
        </span>
        <span style="float: right !important;" class="mr-3">
          <a :href="github" target="_blank">
            <i class="text-right fa fa-github mr-4"></i>
          </a>
          <a :href="linkedin" target="_blank">
            <i class="text-right fa fa-linkedin"></i>
          </a>
        </span>
      </div>
  </div>

  <MoviesPage />
  
  <div class="footer">
    <p>© 2022 Copyright: <span style="color: green">Medforum zadania rekrutacyjne front-end 12.2022</span></p>
  </div>
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@4.3.1/dist/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">
  <link rel="stylesheet" type="text/css" href="https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css" />
  <link rel="preconnect" href="https://fonts.googleapis.com"><link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Oswald:wght@200&display=swap" rel="stylesheet" />
</template>


<script>
import MoviesPage from './components/Movies-page.vue'

export default {
  name: 'App',
  components: {
    MoviesPage
  },
  data() { return { 
    github: 'https://github.com',
    linkedin: 'https://linkedin.com'
  }; },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Oswald:wght@200&display=swap');

i { 
  cursor: pointer;
}

.custom-navbar-brand {
  font-size: 30px !important;
  padding: 5px;
}

.custom-navbar {
  width: 100% !important;
  height: 60px;
  background-color: black;
}

a {
  color: white !important;
}

a:hover {
  text-decoration: none !important;
  color: red !important;
}

.fa-github, .fa-linkedin {
  color: white;
}

.fa-github:hover, .fa-linkedin:hover {
  color: rgb(37, 37, 242);
}

.footer {
  position: sticky;
  top: calc( 100vh - 50px );
  width:100%;
  background-color: black;
  height: 50px;
}

p {
  color: white;
  padding-top: 10px;
  font-size: 18px;
  letter-spacing: 2px;
}

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  background-color: rgb(35, 34, 34);
  font-family: 'Oswald', sans-serif;
  min-height: 1000px;
}
</style>
