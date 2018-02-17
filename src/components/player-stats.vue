<style scoped>
  div.content__card {
    border: solid 2px grey;
    margin: 0.5rem;
  }

  input.label {
    border: none;
    font-weight: bolder;
    margin: 0;
    padding: 0.5rem;
    text-align:center;
  }

  li.divider {
    border-bottom: 2px solid grey;
    height: 2px;
    margin-top: 1.5rem;
    width: 80%;
  }

  button.operator__button {
    background-color: lavender;
    border: none;
    font-size: 3.2rem;
    font-weight: bolder;
    height: 2rem;
    width: 4rem;
  }

  span.stat__span {
    font-size: 4rem;
    padding: 0 1rem;
  }
</style>

<template>
  <div class="content__card">
    <div class="navbar">
      <ul>
        <li>
          <input class="label" type="text" :placeholder="'Player #' + playerNumber + '\'s Name Here.'" />
        </li>
        <li class="divider"></li>
        <li>
          <button @click="subtractFrom" type="button" class="operator__button">-</button>
          <span class="stat__span">{{ stat }}</span>
          <button @click="addTo" type="button" class="operator__button">+</button>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
  export default {
    name: "player-stats",

    data() {
      return {
        stat: 0,
      };
    },

    props: {
      startingCount: {
        type: Number,
        required: false,
      },
      playerNumber: {
        type: Number,
        required: true,
      }
    },

    mounted() {
      this.stat = this.startingCount;
    },

    methods: {
      subtractFrom() {
        this.stat -= 1;
      },

      addTo() {
        this.stat += 1;
      }
    },
  }
</script>
