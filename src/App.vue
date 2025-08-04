<script>
export default {
  data() {
    return {
      city: ""
    };
  },
  computed: {
    cityName() {
      return "✻" + this.city + "✻"
    }
  },
  methods: {
    getWeather() {
      alert("Some weather API call would go here for " + this.city);
    }
  }
}

</script>

<template>
  <div class="wrapper">
    <h1>Wetter-App</h1>
    <p>Erfahre das aktuelle Wetter in {{ city == "" ? "Deiner Stadt ⛅️" : cityName }}</p>
    <input v-model="city" type="text" placeholder="Gib deine Stadt ein" />
    <button v-if="city != ''" @click="getWeather()">Wetter anzeigen</button>
    <button v-else disabled>Stadt eingeben, um das Wetter zu sehen</button>
    <p>Hier wird das Wetter angezeigt.</p>
  </div>
</template>

<style scoped>
.wrapper {
  width: 900px;
  height: 500px;
  border-radius: 50px;
  background: linear-gradient(339deg, rgba(137, 248, 250, 0.804) 0%, rgba(197, 146, 190, 0.901) 100%);
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
  font-family: 'Arial', sans-serif;
  font-size: 18px;
  transition: background 0.5s ease;
}

.wrapper h1 {
  margin-top: 50px;
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
  font-size: 14px;
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
</style>
