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
  <div id="app">
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: 'app'
}
</script>

<style>
  @import '../node_modules/bulma/css/bulma.css';
  html {
    background-color: #666;
  }
  body {
    margin-top:4em;
  }
</style>
