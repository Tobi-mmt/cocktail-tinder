<template>
  <div id="app">
    <div v-on:click="() => toggleList()">
      <LikeCounter :counter="likedCocktails.length" />
    </div>
    <LikeList :cocktails="likedCocktails" v-if="viewList" :deleteCocktail="deleteCocktail" />
    <CardWraper :likeCocktail="likeCocktail" v-if="!viewList"/>
  </div>
</template>

<script>
import CardWraper from "./components/CardWraper.vue";
import LikeCounter from "./components/LikeCounter.vue";
import LikeList from "./components/LikeList.vue";

export default {
  name: "app",
  components: {
    CardWraper,
    LikeCounter,
    LikeList
  },
  data: function() {
    return {
      likedCocktails: [],
      viewList: false
    };
  },
  methods: {
    likeCocktail: function(drink) {
      const storage = JSON.parse(localStorage.getItem('likedCocktails'))
      const drinks = storage || []
      drinks.push(drink);
      localStorage.setItem('likedCocktails', JSON.stringify(drinks))
      this.likedCocktails = drinks
    },
    toggleList: function() {
      this.viewList = !this.viewList;
    },
    deleteCocktail: function(cocktailIdx) {
      const drinks = JSON.parse(localStorage.getItem('likedCocktails'))
      drinks.splice(cocktailIdx, 1)
      localStorage.setItem('likedCocktails', JSON.stringify(drinks))
      this.likedCocktails = drinks
    }
  },
  created: function() {
    const storage = JSON.parse(localStorage.getItem('likedCocktails'))
    this.likedCocktails = storage || []
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
