<script>
export default {
  data() {
    return {
      city: ""
    };
  }
}

</script>

<template>
  <div class="wrapper">
    <h1>Wetter-App</h1>
    <p>Erfahre das aktuelle Wetter in {{ city }} Stadt.</p>
    <input v-on:input="this.city = $event.target.value" type="text" placeholder="Gib deine Stadt ein" />
    <button>Wetter anzeigen</button>
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
  border: 0;
  border-bottom: 2px solid #110813;
  color: #860a6f;
  font-size: 14px;
  padding: 5px 8px;
  outline: none;
}

.wrapper input:focus {
  border-bottom-color: #6e3d7d;
}

.wrapper button {
  background: #e3bc4b;
  color: #531c02;
  border-radius: 10px;
  border: 2px solid #b99935;
  padding: 10px 15px;
  margin-left: 20px;
  cursor: pointer;
  transition: transform 500ms ease;
}

.wrapper button:hover {
  transform: scale(1.1) translateY(-5px);
}
</style>
