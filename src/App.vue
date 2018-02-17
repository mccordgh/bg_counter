<style>
  html, body {
    background-color: lavender;
    font-size: 10px;
    /*height: 100%;*/
    /*width: 100%;*/
    padding: 0.5rem;
    margin: 0;
  }

  div.navbar {
    background-color: lavender;
    overflow: hidden;
    padding: 1rem;
    text-align: center;
  }

  div.navbar ul {
    height: 100%;
    margin: 0;
    padding: 0;
  }

  div.navbar ul li {
    cursor: pointer;
    display: inline-block;
    font-size: 2rem;
    font-weight: bolder;
    height: 2rem;
    margin: 0;
    padding: 0;
    width: 100%;
  }

  div.navbar ul li:hover {
    color: darkgrey;
  }
</style>

<template>
  <div>
    <div class="navbar">
      <ul>
        <li @click="addPlayer">+ Add Player +</li>
      </ul>
    </div>
    <div class="content">
      <template v-for="num in playerCount">
        <player-stats
          v-bind:key="num"
          :starting-count="statStartingCount"
          :player-number="num"
        >
        </player-stats>
      </template>
    </div>
  </div>
</template>

<script>
  import PlayerStats from '../src/components/player-stats.vue';

  export default {
    name: 'app',

    data() {
      return {
        playerCount: 0,
        statStartingCount: 0,
        startingCountCheck: false,
      };
    },

    methods: {
      addPlayer() {
        if (!this.startingCountCheck) {
          this.statStartingCount = parseInt(window.prompt('Stat starting number?', '0'), 10);

          if (isNaN(this.statStartingCount)) {
            this.statStartingCount = 0;
          }

          this.startingCountCheck = true;
        }

        this.playerCount += 1;
      },
    },

    components: { PlayerStats },
  }
</script>


