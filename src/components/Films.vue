<template>
  <div id="films">
    <div v-for="(film, index) in films" :key="index" class="selectedFilm">
      <router-link v-bind:to="'/films/' + parseInt(index+1) ">
        <div v:bind:id="1">{{film.title}}</div>
      </router-link>
    </div>
  </div>
</template>

<script>
/*
export default {
  data() {
    return {
      films: [],
      id: ""
    };
  },
  methods: {},
  created() {
    fetch("https" + "://swapi.dev/api/films/")
      .then(response => response.json())
      .then(data => {
        this.films = data.results;
      });
  }
};
*/
export default {
///var proxyUrl = 'https:/swapi.dev/api/',
//targetUrl = 'films',
  data() {
    return {
      films: [],
      id: ""
    };
  },
  mounted() {
    this.fetchData()
  },
  watch: {
    // call again the method if the route changes
    '$route': 'fetchData'
  },
  methods: {
    fetchData(){
      //var proxyUrl = 'https://swapi.dev/api/';
      //var targetUrl = 'films';
      //fetch("https:/swapi.dev/api/films/")
    fetch("https:/swapi.dev/api/films/")
      .then(response => response.json())
      .then(data => {
        this.films = data.results;
      });
    }
  }
};

</script>

<style >
#films {
  columns: 200px 2;
  column-gap: 30px;
  column-rule: 1px solid black;
  column-span: all;  
  
  width: 100%;
  border: 2px solid #ccc;
  padding: 10px;
  margin-bottom: 30px;
  max-width: 35%;
  margin: 10% auto;
}

.selectedFilm {   
  text-align: center;
  width: 100%;
  font-size: 1.4vw;
  padding: 10px;
  margin: 0px 0;
  border: 1px solid black;
  box-sizing: border-box;
  background: lightblue;
}
</style>