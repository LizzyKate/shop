<template>
  <div id="app">
    <hello></hello>
    <ban></ban>
    <about></about>
    <search></search>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue';
import ban from './components/banner';
import about from './components/about';
import filter from './components/filter';
import  './assets/main.css';
import  './assets/fonts/css/all.css';

export default {
  components:{
    hello:HelloWorld,
    ban:ban,
    about:about,
    search:filter
  }
}
</script>

<style>

</style>
