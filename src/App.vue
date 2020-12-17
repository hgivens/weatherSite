<template>
  <div id="app">
    <Header title= 'Weather Checker'></Header>
    <Unit v-on:units="getUnitType($event)"></Unit>
    <Weather v-bind:weatherdata='weatherData' v-bind:weatherimg='weatherImg' v-on:zip="getUserZip($event)" ></Weather>
    <Footer></Footer>
  </div>
</template>

<script>
//MY IMPORTS FOR LINKING PAGES AND AXIOS
import Header from './components/Header.vue'
import Weather from './components/Weather.vue'
import Footer from './components/Footer.vue'
import Unit from './components/Unit.vue'

import axios from 'axios';


export default {
  name: 'App',
  components: {
    Header,
    Weather,
    Footer,
    Unit,
  },
  data(){
    return{
      weatherData: '',
      zip: '65804',
      weatherImg: '',
      units: 'imperial',
    };
  },
  methods:{
   //THIS SETS THE ZIP TO WHAT THE USER INPUT 
    getUserZip(theInput){
      this.zip = theInput;
      
    },
    //THIS SETS UNITS TO EITHER IMPERIAL OR METRIC THEY START OFF AS STANDARD
     getUnitType(theInput){
       console.log("input: "+theInput);
       this.units = theInput;
       
    },
    
  },
  mounted(){
    axios.get(`https://api.openweathermap.org/data/2.5/weather?zip=${this.zip},us&units=${this.units}&appid=8ccc67cbf2fc8f7352903633cb91e4fc`)
    .then((response) => {
      this.weatherData = response.data;
      this.weatherImg = 'http://openweathermap.org/img/wn/'+this.weatherData.weather[0].icon+'@2x.png'
    });
  }
}
</script>

<style>
*{
  margin: 0%;
  padding: 0%;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
