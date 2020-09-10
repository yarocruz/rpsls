<template>
  <div class="container">
    <h2 class="computer-win-counts">{{ computerWins }}</h2>
    <h2 class="user-win-counts">{{ userWins }}</h2>
    <div class="game-board">
      <h1 class="computer-guess">{{ computerGuess ? computerGuess : 'Make a Move' }}</h1>
      <ul class="emojis">

        <li class="emoji" v-for="emoji in emojis" v-bind:key="emoji.name" @click="clickIt(emoji.symbol)">
          {{ emoji.symbol }}
          <span class="name">{{ emoji.name}}</span>
        </li>
      </ul>
    </div>
   <h1>Rules</h1>
    <ul class="rules">
      <li>Scissors cuts Paper</li>
      <li>Paper covers Rock</li>
      <li>Rock Crushes Lizard</li>
      <li>Lizard Poisons Spock</li>
      <li>Spock smashes Scissors</li>
      <li>Scissors decapitates Lizard</li>
      <li>Lizard Eats Paper</li>
      <li>Paper Disproves Spock</li>
      <li>Spock vaporizes Rock</li>
      <li>and as always, Rock crushes Scissors</li>
    </ul>
  </div>
</template>

<script>
  export default {
    name: 'Game',
    data () {
      return {
        emojis: [
          {
            name: 'Rock',
            symbol: '👊'
          },
          {
            name: 'Paper',
            symbol: '✋'
          },
          {
            name: 'Scissor',
            symbol: '✌️'
          },
          {
            name: 'Lizard',
            symbol: '🦎'
          },
          {
            name: 'Spock',
            symbol: '🖖'
          },
        ],
        computerGuess: '',
        computerWins: 0,
        userWins: 0,
      }
    },
    methods: {
      clickIt: function (selection) {
        let computerGuess = this.emojis[Math.floor(Math.random() * this.emojis.length)]
        this.computerGuess = computerGuess.symbol
        console.log(selection)
        if (
            (selection === '👊' && this.computerGuess === '✌️') ||
            (selection === '✌️' && this.computerGuess === '✋') ||
            (selection === '✋' && this.computerGuess === '👊') ||
            (selection === '👊' && this.computerGuess === '🦎') ||
            (selection === '🦎' && this.computerGuess === '🖖') ||
            (selection === '✌️' && this.computerGuess === '🦎') ||
            (selection === '🦎' && this.computerGuess === '✋') ||
            (selection === '✋️' && this.computerGuess === '🖖') ||
            (selection === '🖖' && this.computerGuess === '👊')
          ) {
          this.userWins += 1
          console.log(selection, this.computerGuess)
        } else if (selection === computerGuess.symbol) {
          console.log('Tied')
        } else {
          this.computerWins += 1
          console.log(selection, this.computerGuess)
        }

      },
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
    transition: transform 0.5s ease-in-out;
  }
  .emojis li:hover {
    cursor: pointer;
    transform: scale(1.3);
  }
  .emoji {
    display: flex;
    flex-direction: column;
  }
  .name {
    font-size: 12px;
    font-weight: bold;
  }
  .computer-guess {
    font-size: 80px;
  }
  .game-board {

  }
  .rules {
    list-style: none;
    text-align: center;
    padding: 0;
  }
  .rules li {
    margin: 10px auto;
  }
  .user-win-counts,
  .computer-win-counts {
    position: absolute;
    left: 10px;
    margin: 40px;
  }
  .user-win-counts {
    top: 530px;
  }
</style>