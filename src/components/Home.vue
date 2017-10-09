<!--
    ________                           ____        __      __             __
   / ____/ /_  ____ _____  _______  __/ __ \____  / /_  __/ /_  ___  ____/ /________ _
  / /   / __ \/ __ `/ __ \/ ___/ / / / /_/ / __ \/ / / / / __ \/ _ \/ __  / ___/ __ `/
 / /___/ / / / /_/ / / / / /__/ /_/ / ____/ /_/ / / /_/ / / / /  __/ /_/ / /  / /_/ /
 \____/_/ /_/\__,_/_/ /_/\___/\__, /_/    \____/_/\__, /_/ /_/\___/\__,_/_/   \__,_/
                             /____/              /____/

 Copyright ? 2017 D.E. Goodman-Wilson

-->

<template>
  <columns is-mobile>
    <column is-half is-offset-one-quarter>
      <img src="../assets/ChancyPolyhedra.png" v-bind:srcset="`${logos.small} 1x, ${logos.big} 2x`">
      <h2 class="has-text-centered">Roll 2d6 for awesomeness.</h2>
      <div class="field has-addons">
        <div class="control is-expanded">
          <input class="input" id="dice" type="text" placeholder="2d6" v-on:keyup.13="roll">
        </div>
        <div class="control">
          <button class="button is-primary" v-on:click="roll">
            Roll!
          </button>
        </div>
      </div>
      <div class="field has-text-centered">
        <label id="result">{{ result }}</label>
      </div>
    </column>
  </columns>
</template>

<script>
  var logos = {
    small: require('../assets/ChancyPolyhedra.png'),
    big: require('../assets/ChancyPolyhedra@2x.png')
  }

  export default {
    name: 'home',
    data () {
      return {
        result: '…'
      }
    },
    computed: {
      logos () { return logos }
    },
    methods: {
      roll: function (event) {
        const vm = this
        var dice = document.querySelector('#dice')
        fetch('https://chancypolyhedra.now.sh/v1/' + dice.value).then(function (response) {
          return response.json()
        }).then(function (data) {
          console.debug(data)
          vm.result = data['result']
        }).catch(function () {
          vm.result = 'there was a problem'
        })
      }
    }
  }
</script>

<style>
  @import url('https://fonts.googleapis.com/css?family=Playfair+Display');

  .field {
    padding: 1em;
    background-color: ghostwhite;
  }

  h2 {
    font-family: Playfair;
    font-size: 50px;
    font-stretch: ultra-condensed;
    color: #ddd;
    margin-bottom: 1em;
  }
</style>
