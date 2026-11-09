<template>
  <div id="nav" >
    <router-link to="/">Home</router-link>
    <router-link to="/about">About</router-link>
    <router-link to="/random-quote">Random Quote</router-link>
    <router-link to="/contact">Contact</router-link>
  </div>
  <div class="container">
    <router-view></router-view>
  </div>

  
</template>

<style lang="css">

  #nav .active-Link {
    color: #333;
    font-weight: bold;
  }

</style>


