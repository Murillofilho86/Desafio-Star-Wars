<template>
  <div>
    <transition name="page">
      <router-view></router-view>
    </transition>
  </div>
</template>

<script>
</script>

<style>
.body {
  font-family: "Open Sans", "Helvetica Neue", Arial, sans-serif;
  color: #ffffff;
  background: #000 url(https://bit.ly/2JWFGPM);
}

* {
  cursor: url(https://bit.ly/2taGCWz), auto !important;
}

.page-enter,
.page-leave-active {
  opacity: 0;
}

.page-enter-active,
.page-leave-active {
  transition: opacity 0.05s;
}



</style>
