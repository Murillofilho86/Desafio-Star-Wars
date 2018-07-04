<template>
<div>
  <panel-intro />
  <panel-title />
  <panel-planets v-show="loaded" :planets="planets" />
  <panel-loading v-show="!loaded" />
  <button v-on:click="userClick" name="btn" v-show="loaded">Next Planet</button> 

 
 </div>
</template>

<script>
import Planets from "../panel/Planets.vue";
import Intro from "../panel/Intro.vue";
import Title from "../panel/Title.vue";
import Loading from "../Shared/Loading";

export default {
  components: {
    "panel-intro": Intro,
    "panel-planets": Planets,
    "panel-title": Title,
    "panel-loading": Loading
  },

  name: "app",
  data() {
    return {
      planets: [],
      imgLoad: "../src/assets/darth_vader.gif",
      loaded: false,
      url: "https://swapi.co/api/planets/"
    };
  },

  methods: {
    userClick: function() {
      this.loaded = false;
      this.$http
        .get(this.url + (Math.floor(Math.random() * this.url.length - 1) + 1))
        .then(res => res.json())
        .then(planets => (this.planets = planets), err => console.log(err))
        .finally(() => {
          this.loaded = true;
        });
    }
  },

  created() {
    setTimeout(() => {
      this.loaded = false;
      this.$http
        .get(this.url + (Math.floor(Math.random() * (this.url.length - 1)) + 1))
        .then(res => res.json())
        .then(planets => (this.planets = planets), err => console.log(err))
        .finally(() => {
          this.loaded = true;
        });
    }, 16000);
  }
};
</script>

<style>
body {
  font-family: "Open Sans", "Helvetica Neue", Arial, sans-serif;
  color: #ffffff;
  background: #000 url(//cssanimation.rocks/demo/starwars/images/bg.jpg);
}

button {
  margin-top: 1%;
  margin-left: 40%;
  position: relative;
  animation-name: example;
  animation-duration: 3s;
  animation-delay: 12s;
  z-index: 9999;
}
</style>
