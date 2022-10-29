<template>
  <div>
    <h1>{{ heading }}</h1>
    <button @click="getCurrentWeather()">Display current weather data</button>

    <div id="locationData">
      <p>Latitude: {{ weatherData.latitude }}</p>
      <p>Longitude: {{ weatherData.longitude }}</p>
      <p>
        Timezone: {{ weatherData.timezone }}
        {{ weatherData.timezone_abbreviation }}
      </p>
    </div>
    <div id="currentWeatherData">
      <p>Temperature: {{ currentWeather.temperature }}</p>
      <p>Windspeed: {{ currentWeather.windspeed }}</p>
      <p>Wind direction: {{ currentWeather.winddirection }}</p>
      <p>Weather code: {{ currentWeather.weathercode }}</p>
      <p>Time: {{ currentWeather.time }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "WeatherComponent",
  data() {
    return {
      heading: "Weather in Amsterdam",
      weatherData: "",
      currentWeather: "",
    };
  },
  methods: {
    getCurrentWeather() {
      fetch(
        "https://api.open-meteo.com/v1/forecast?latitude=52.3738&longitude=4.8910&hourly=temperature_2m&current_weather=true"
      )
        .then((data) => data.json())
        .then((json) => (this.weatherData = json))
        .then((current) => (this.currentWeather = current.current_weather));
    },
  },
};
</script>
