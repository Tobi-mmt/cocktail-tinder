<template>
  <div id="app">
    <div v-on:click="() => toggleList()">
      <LikeCounter :counter="likedCocktails.length" />
    </div>
    <LikeList :cocktails="likedCocktails" v-if="viewList" />
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
      this.likedCocktails.push(drink);
    },
    toggleList: function() {
      this.viewList = !this.viewList;
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
