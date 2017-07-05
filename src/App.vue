<template>
  <div class="container" id="app">
    <h1 class="text-primary">TTS Demo</h1>
      <h5 class="text-muted">powered by <a href="https://vuejs.org/">Vue.js</a> and <a href="https://responsivevoice.org/">ResponsiveVoice.js</a></h5>
      <div style="margin-top: 100px"></div>
    <InputForm @inputFormSubmit="speakIt"></InputForm>
  </div>
</template>

<script>
import InputForm from './components/InputForm'

export default {
  name: 'app',
  components: {
    InputForm
  },
  methods: {
    speakIt: function (text) {
      responsiveVoice.speak(text)
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
