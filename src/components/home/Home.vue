<template>
<div>
  <panel-intro />
  <panel-title />
  <panel-planets v-show="loading" :planets="planets" />
  <panel-loading v-show="!loading"/>

  <button v-on:click="userClick" name="btn" v-show="loading">Next Planet</button> 

  <audio :src="sound" autoplay loop></audio>
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
      title: "Aqui começa a sua jornada. Que a força esteja com você!",
      planets: [],
      imgLoad: "../src/assets/darth_vader.gif",
      loading: false,
      url: "https://swapi.co/api/planets/"
      //, sound: 'https://bit.ly/2xZ7qZq'
    };
  },

  methods: {
    userClick: function() {
      this.loading = false;
      this.$http
        .get(this.url + (Math.floor(Math.random() * this.url.length - 1) + 1))
        .then(res => res.json())
        .then(planets => (this.planets = planets), err => console.log(err))
        .finally(() => {
          this.loading = true;
        });
    }
  },

  created() {
    this.loading = false;
    this.$http
      .get(this.url + (Math.floor(Math.random() * (this.url.length - 1)) + 1))
      .then(res => res.json())
      .then(planets => (this.planets = planets), err => console.log(err))
      .finally(() => {
        this.loading = true;
      });
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
