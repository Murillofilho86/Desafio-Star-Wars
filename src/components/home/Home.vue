<template>
<div>
  <panel-intro></panel-intro>
  <panel-title></panel-title>
  <panel-planets v-show="loading" :planets="planets" class="panel-planets"/>
  <button v-on:click="userClick" v-if="loading">Next Planet</button> 

 <audio :src="sound" autoplay loop></audio>
 </div>
</template>


<script>
import Planets from "../panel/Planets.vue";
import Intro from "../panel/Intro.vue";
import Title from "../panel/Title.vue";

export default {
  components: {
    "panel-intro": Intro,
    "panel-planets": Planets,
    "panel-title": Title
  },

  name: "app",
  data() {
    return {
      title: "Aqui começa a sua jornada. Que a força esteja com você!",
      planets: [],
      imgLoad: "../src/assets/darth_vader.gif",
      loading: false,
      url: "https://swapi.co/api/planets/"
      // sound: 'https://bit.ly/2xZ7qZq'
    };
  },

  methods: {
    userClick: function() {
      this.loading = false;
      this.$http
        .get(this.url + (Math.floor(Math.random() * this.url.length) + 1))
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
}

.intro_animacao {
  animation: intro 2s ease-out 0s;
}
.intro {
  position: absolute;
  top: 40%;
  left: 20%;
  z-index: 1;
  opacity: 0;
}

.panel-planets{
  text-align: center;
  margin-top: 20%
}
img.loading {
  text-align: center;
  opacity:0.65;
	-moz-opacity: 0.65;
	filter: alpha(opacity=65);
}


.panel-fade-enter, .panel-fade-leave-active{
    opacity: 0;
}

.panel-fade-enter-active, .panel-fade-leave-active{
  transition: opacity .05s;
}


</style>
