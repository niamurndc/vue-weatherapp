<template>
  <div class="main">
    <input type="text" v-model="city"> <button @click="getWeath">Get Weather</button>
    <div v-if="typeof weather.main != 'undefined'" class="box">
      <h2>{{weather.name}}, {{weather.sys.country}}</h2>
      <h1>{{ Math.round(weather.main.temp)}}<span> &deg;c</span></h1>
      <i v-if="weather.weather[0].description == 'overcast clouds' || weather.weather[0].description == 'broken clouds'" class="fas fa-cloud"></i>
      <i v-if="weather.weather[0].description == 'rain' || weather.weather[0].description == 'heavy intensity rain' || weather.weather[0].description == 'moderate rain'" class="fas fa-cloud-rain"></i>
      <i v-if="weather.weather[0].description == 'haze' || weather.weather[0].description == 'scattered clouds' || weather.weather[0].description == 'few clouds'" class="fas fa-cloud-sun"></i>
      <i v-if="weather.weather[0].description == 'mist' || weather.weather[0].description == 'clear sky'" class="fas fa-sun"></i>
      <h3>{{weather.weather[0].description}}</h3>
    </div>
  </div>
</template>

<script>
import Vue from 'vue'
import axios from 'axios'
import VueAxios from 'vue-axios'
 
Vue.use(VueAxios, axios)
export default {
  name: 'Main',
  data(){
    return{
      app_key: 'a783959171432df2b90b278e51620848',
      app_url: 'https://api.openweathermap.org/data/2.5/',
      city: '',
      weather: {}

    }
  },

  methods: {
    getWeath(){
      Vue.axios.get(`${this.app_url}weather?q=${this.city}&units=metric&appid=${this.app_key}`)
      .then(res => {
        this.weather = res.data;
        console.log(res.data);
      })
      .catch(err => console.log(err));
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.main{
  width: 900px;
  margin: 0 auto;
  padding: 100px 0 ;
  text-align: center;
}

input{
  height: 20px;
  border-radius: 5px;
  color: #777;
  font-size: 20px;
  font-weight: bold;
  widows: 200px;
  border: none;
  padding: 10px;
  border: 1px solid #999;
  margin-top: 5px;
}

button{
  background: rgb(32, 32, 34);
  color: #fff;
  padding: 12px;
  border-radius: 5px;
  font-size: 16px;
  border: none;
}

.box{
  background: rgba(0, 0, 0, 0.2);
  width: 420px;
  margin: 40px auto;
  border-radius: 10px;
  font-family: Arial, Helvetica, sans-serif;
}

h1{
  color: #fff;
  margin: 40px 0;
  font-size: 126px;
}

span{
  color: #fff;
  margin: 20px 0;
  font-size: 86px;
}

h2{
  color: #444;
  margin: 20px 0;
  font-size: 46px;
}

h3{
  color: #fff;
  font-size: 46px;
}

i{
  color: #fff;
  font-size: 90px;
}
</style>
