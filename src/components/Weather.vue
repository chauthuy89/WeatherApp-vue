<template>
  <div class="weather">
    <h1 class="cyan--text text-center pa-3" > Weather App</h1>
    <button v-on:click="getWeatherData" >Get Weather Data</button>
    <div v-for="weatherData in weatherDataList" :key="weatherData.id" class="weather-data">
      <div class="weather-stats">
        <div>
          <span>{{weatherData.time}}</span>
        </div>
        <div>
          <span class="location">{{weatherData.location}}</span>
        </div>
      </div>
      <div class="weather-icon">
        <img :src="`https://www.metaweather.com/static/img/weather/${weatherData.abbr}.svg`">
      </div>
      <div class="weather-temp">
        <span>{{weatherData.temp}}°</span>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: "Weather",
  data() {
    return {
      weatherDataList: []
    };
  },
  methods: {
    getWeatherData() {
    //   fetch("weather.json")
    //     .then(response => response.json())
    //     .then(data => (this.weatherDataList = data));
         axios.get("weather.json").then(response => (this.weatherDataList = response.data));
    }
  }
};
</script>
<style scoped>
.weather-data {
  display: flex;
  align-items: center;
  margin-top: 20px;
  margin-left: 20px;
  border-bottom: 2px solid #ccc;
  padding: 20px;
  background:rgb(21, 216, 216);
}

.weather-icon {
  flex-grow: 2;
}

.weather-stats {
  flex-grow: 9;
  text-align: left;
  padding-left: 20px;
}

.weather-stats .location {
  font-size: 30px;
}

.weather-temp {
  flex-grow: 1;
  font-size: 35px;
}

img {
  width: 70px;
}

button {
    padding:10px;
    background-color: cyan;
    color: black;
    border: 2px dashed #ccc;
    margin-left:130px;
}
.weather{
    margin:auto;
    padding:auto;
    width: 80%;
    justify-content: center;
}
</style>