<template>
  <div id="app">
    <img alt="RPSLS logo" src="./assets/rpsls_logo.png">
    <Game />
    <HelloWorld msg="Welcome to Rock Paper Scissor Lizard Spock"/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Game from "@/components/Game";

export default {
  name: 'App',
  components: {
    Game,
    HelloWorld
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
</style>
