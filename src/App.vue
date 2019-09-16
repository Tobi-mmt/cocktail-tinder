<template>
  <div id="app">
    <CardWraper :likeCocktail="likeCocktail" />
  </div>
</template>

<script>
import CardWraper from "./components/CardWraper.vue";

export default {
  name: "app",
  components: {
    CardWraper
  },
  data: function() {
    return {
      likedCocktails: []
    };
  },
  methods: {
    likeCocktail: function(idDrink) {
      this.likedCocktails.push(idDrink);
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
