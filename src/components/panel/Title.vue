<template>
    <div class="starwars-demo" v-on:mouseover="scrollDireita()" >
        <img src="//cssanimation.rocks/demo/starwars/images/star.svg" alt="Star" class="star">
        <img src="//cssanimation.rocks/demo/starwars/images/wars.svg" alt="Wars" class="wars">
    </div>
</template>

<script>
export default {
  methods: {}
};
</script>

<style>
.star {
  animation: star 10s ease-out;
  animation-delay: 7s;
  opacity: 0;
}
.wars {
  animation: wars 10s ease-out;
  animation-delay: 7s;
  opacity: 0;
}

@keyframes star {
  0% {
    opacity: 0;
    transform: scale(1.5) translateY(-0.75em);
  }
  20% {
    opacity: 1;
  }
  89% {
    opacity: 1;
    transform: scale(1);
  }
  100% {
    opacity: 0;
    transform: translateZ(-1000em);
  }
}

@keyframes wars {
  0% {
    opacity: 0;
    transform: scale(1.5) translateY(0.5em);
  }
  20% {
    opacity: 1;
  }
  90% {
    opacity: 1;
    transform: scale(1);
  }
  100% {
    opacity: 0;
    transform: translateZ(-1000em);
  }
}

.starwars-demo {
  perspective: 800px;
  transform-style: preserve3d;
  animation-delay: 16s;
}

.starwars-demo {
  height: 17em;
  left: 50%;
  position: absolute;
  top: 53%;
  transform: translate(-50%, -50%);
  width: 34em;
}

img {
  width: 100%;
}

.star,
.wars {
  position: absolute;
}

.star {
  top: -0.75em;
}

.wars {
  bottom: -0.5em;
}

@media only screen and (max-width: 600px) {
  .starwars-demo {
    font-size: 10px;
  }
}

@media only screen and (max-width: 480px) {
  .starwars-demo {
    font-size: 7px;
  }
}
</style>
