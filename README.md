# ⛵🇳🇱 weather-amsterdam

A Vue app that renders the current weather data for the Dutch city of Amsterdam.

## ⚙️ Codebase

1. In the WeatherComponent, we fetch the data from the Weather Forecast API for the current weather data in Amsterdam which is displayed in the component.

1.1 We first fetch the data using the fetch API:

```
methods: {
    getCurrentWeather() {
      fetch(
        "https://api.open-meteo.com/v1/forecast?latitude=52.3738&longitude=4.8910&hourly=temperature_2m&current_weather=true"
      )
        .then((data) => data.json())
        .then((json) => (this.weatherData = json))
        .then((current) => (this.currentWeather = current.current_weather));
    },
  }
```

Since the JSON object in the API has different objects and properties, I decided to set data from the different objects and their properties to two different data properties: weatherData and currentWeather.

2. Then, the data from the different properties is displayed in two seperate container divs: one for the location data and the other one for the weather data

```
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
```

2.1 This data is then visible after the getCurrentWeather event is triggered with the "Display current weather data" button:

```
<button @click="getCurrentWeather()">Display current weather data</button>
```

3. After this, the browser then displays the data from the API, which should look like this:

<img width="200" alt="Screenshot 2022-10-29 at 15 31 56" src="https://user-images.githubusercontent.com/72168158/198837151-0d1891a0-22f1-42b4-923b-7a74d8621019.png">

🎉🎉🎉

## 📚 Useful resources

- Weather Forecast API: https://open-meteo.com/en/docs#latitude=52.3738&longitude=4.8910&hourly=temperature_2m&current_weather=true
- Fetch API in Vue: https://www.koderhq.com/tutorial/vue/http-fetch/
- Fetch API: https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
