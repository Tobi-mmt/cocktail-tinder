<template>
  <div id="card-wrapper">
    <div class="controler">
      <md-button
        class="md-icon-button md-accent"
        v-on:click="() => {
            animateBox('left')
            getRandomCocktail()
          }"
      >
        <Icon name="times" scale="4.5" style="color: red" />
      </md-button>
      <md-button
        class="md-icon-button md-primary"
        v-on:click="() => {
            likeCocktail(cocktail.idDrink)
            animateBox('right')
            getRandomCocktail()
          }"
      >
        <Icon name="check" scale="4" style="color: green" />
      </md-button>
    </div>
    <div class="cards">
      <AnimationBox
        v-for="(cocktail, idx) in cocktails"
        v-bind:key="cocktail.idDrink"
        :animation="idx == (cocktails.length -1) ?  animation : 'stop' "
      >
        <Card :cocktail="cocktail" />
      </AnimationBox>
    </div>
  </div>
</template>

<script>
import Card from "./Card.vue";
import axios from "axios";
import AnimationBox from "./AnimationBox";
import "vue-awesome/icons/check";
import "vue-awesome/icons/times";
import Icon from "vue-awesome/components/Icon";

export default {
  name: "CardWraper",
  components: {
    Card,
    AnimationBox,
    Icon
  },
  props: ["likeCocktail"],
  data: function() {
    return {
      animation: "stop",
      cocktails: []
    };
  },
  methods: {
    animateBox: function(direction) {
      this.animation = direction;
      setTimeout(() => {
        this.animation = "stop";
        this.cocktails.pop();
      }, 1000);
    },
    getRandomCocktail: function() {
      axios
        .get("https://www.thecocktaildb.com/api/json/v1/1/random.php")
        .then(response => {
          this.cocktails.unshift(response.data.drinks[0]);
        });
    }
  },
  mounted: function() {
    axios
      .get("https://www.thecocktaildb.com/api/json/v1/1/random.php")
      .then(response => {
        this.cocktails.unshift(response.data.drinks[0]);
      });
    axios
      .get("https://www.thecocktaildb.com/api/json/v1/1/random.php")
      .then(response => {
        this.cocktails.unshift(response.data.drinks[0]);
      });
  }
};
</script>

<style lang="scss" scoped>
.md-button {
  margin: 0 3em;
  width: 90px;
  height: 90px;
}
#card-wrapper {
  display: flex;
  position: relative;
  height: 100vh;
  width: 100vw;
  flex-direction: column;
  overflow: hidden;
}
.cards {
  position: relative;
  width: 100%;
}
.controler {
  z-index: 99;
  margin: 2em;
}
</style>