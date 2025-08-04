<script>
import axios from "axios";

export default {
  data() {
    return {
      city: "",
      error: "",
      info: null,
    };
  },
  computed: {
    cityName() {
      return "✻" + this.city + "✻";
    },
    showTemp() {
      return this.info
        ? `Temperatur in ${this.city}: + ${this.info.main.temp} °C`
        : "";
    },
    showFeelsLike() {
      return this.info
        ? `Gefühlte Temperatur: ${this.info.main.feels_like} °C`
        : "";
    },
    showMinTemp() {
      return this.info
        ? `Minimale Temperatur: ${this.info.main.temp_min} °C`
        : "";
    },
    showMaxTemp() {
      return this.info
        ? `Maximale Temperatur: ${this.info.main.temp_max} °C`
        : "";
    },
  },
  methods: {
    getWeather() {
      if (this.city.trim().length < 2) {
        this.error = "Bitte gib eine gültige Stadt ein.";
        setTimeout(() => {
          this.error = "";
        }, 2500);
        return false;
      }
      this.error = "";
      axios
        .get(
          `https://api.openweathermap.org/data/2.5/weather?q=${this.city}&units=metric&appid=a2df5f4957cd5aefcf16fff215d98e6f`
        )
        .then((res) => (this.info = res.data));
      alert("Wetterdaten werden geladen für: " + this.city);
    },
  },
};
</script>

<template>
  <div class="wrapper">
    <h1>Wetter-App</h1>
    <p>
      Erfahre das aktuelle Wetter in
      <b
        ><u>{{
          city == "" ? "Deiner Stadt ⛅️" : cityName.toUpperCase()
        }}</u></b
      >
    </p>
    <input v-model="city" type="text" placeholder="Gib deine Stadt ein" />
    <button v-if="city != ''" @click="getWeather()">Wetter anzeigen</button>
    <button v-else disabled>Stadt eingeben, um das Wetter zu sehen</button>
    <p class="error">{{ error }}</p>

    <div v-show="info != null" style="color: brown">
      <p>
        <b
          ><u>{{ showTemp }}</u></b
        >
      </p>
      <p>{{ showFeelsLike }}</p>
      <p>{{ showMinTemp }}</p>
      <p>{{ showMaxTemp }}</p>
    </div>
  </div>
</template>

<style scoped>
.wrapper {
  width: 900px;
  height: 500px;
  border-radius: 50px;
  background: linear-gradient(
    339deg,
    rgba(137, 248, 250, 0.804) 0%,
    rgba(197, 146, 190, 0.901) 100%
  );
  padding: 20px;
  text-align: center;
  color: #036014;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.2);
  margin: 50px auto;
  font-family: "Arial", sans-serif;
  font-size: 18px;
  transition: background 0.5s ease;
}

.wrapper h1 {
  margin-top: 50px;
  color: #ad1d92;
  font-family: 20px;
}

.wrapper p {
  margin-top: 20px;
}

.wrapper input {
  margin-top: 30px;
  background: transparent;
  text-align: center;
  border: 0;
  border-bottom: 2px solid #110813;
  color: #860a6f;
  font-size: 18px;
  padding: 5px 8px;
  outline: none;
}

.wrapper input:focus {
  border-bottom-color: #b105e6;
}

.wrapper button {
  background: #ddc16d;
  color: #9c0e97;
  border-radius: 10px;
  border: 2px solid #b99935;
  padding: 10px 15px;
  margin-left: 20px;
  cursor: pointer;
  transition: transform 500ms ease;
  margin-top: 20px;
  font-size: 16px;
}

.wrapper button:disabled {
  background: #ccc;
  color: #666;
  cursor: not-allowed;
}

.wrapper button:hover {
  transform: scale(1.1) translateY(-5px);
}

.error {
  color: red;
  margin-top: 20px;
  font-weight: bold;
  font-size: 16px;
  transition: color 0.3s ease;
}
</style>
