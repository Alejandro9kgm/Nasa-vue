<template>
  <div id="app">
    <button @click="apod"> Astronomy Picture of the Day</button>
    <p>{{apodData.date}}</p>
    <img id="apod" :src="apodData.hdurl" alt="">
  </div>
</template>

<script>

export default {
  name: 'App',
  
  data(){
    return{
      name: "8=====D",
      apodData: {},
    }
  },
  methods: {
    apod() {
      fetch('https://api.nasa.gov/planetary/apod?api_key=jsFZytOioyae3IShfceg42zcIAIbpaRUpAlPMmG1').then(response => {
        return response.json()
      }).then(this.setApodData)
    },
    setApodData (results) {
      this.apodData = results;
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

#apod{
  width: 400px;
  height: 400px;
  border: 3px solid pink;
  object-fit: cover;
}

</style>
