<template>
  <div class="container">
    <h1>{{ computerGuess }}</h1>
    <ul class="emojis">

          <li v-for="emoji in emojis" v-bind:key="emoji" @click="clickIt">
            {{ emoji }}
          </li>
    </ul>
    <div class="counter">{{ count }}</div>
    <button @click="startCounter">Start Game</button>
  </div>
</template>

<script>
  export default {
    name: 'Game',
    data () {
      return {
        emojis: ['👊', '✋', '✌️', '🦎', '🖖'],
        count: 0,
        computerGuess: ''
      }
    },
    methods: {
      clickIt: function () {
        const emojis = ['rock', 'paper', 'scissor', 'lizard', 'spock']
        let computerGuess = emojis[Math.floor(Math.random() * emojis.length)]
        this.computerGuess = computerGuess
        console.log(console.log(computerGuess))
      },
      startCounter: function () {
        let timer = setInterval(() => {
          this.count++
          console.log('hello')
          if (this.count > 3) {
            clearInterval(timer)
            this.count = 0
          }
        }, 1000)

      }
    }
  }
</script>

<style>
  .container {
    max-width: 700px;
    margin: 0 auto;
  }
  .emojis {
    display: flex;
    justify-content: space-between;
    list-style: none;
    padding: 0;
  }
  .emojis li {
    font-size: 80px;
  }
  .emojis li:hover {
    cursor: pointer;
    transform: scale(1.5);
  }
</style>