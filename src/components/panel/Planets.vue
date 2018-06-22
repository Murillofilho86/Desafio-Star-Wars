<template>

  <div>
        <div class="planet-table">
            <div class="planet-header">
                <h3>{{ planets.name }}</h3>
            </div>
            <div class="planet-body">
            <p>Population:  {{ planets.population}} </p>
            <p>Climate: {{ planets.climate }}</p>
            <p>Terrain: {{ planets.terrain }}</p>
            <p class="film">Featured in <strong> {{ planets.films.length }} </strong> Films</p>
            </div>
        </div>
  </div>
</template>

<script>
export default {
  
  props: ["planets"]
};
</script>

<style scoped>

.planet-table {
  width: 250px;
  margin: 0 auto;
  text-align: center;
}

.planet-table div {
  border: 1px solid #ffd700;
  padding: 10px;
}

.film {
  text-align: center;
}

</style>
