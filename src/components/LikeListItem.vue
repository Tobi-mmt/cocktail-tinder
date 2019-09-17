strInstructions

<template>
  <md-list-item
    class="md-double-line"
  >
    <md-avatar>
      <img v-bind:src="cocktail.strDrinkThumb" />
    </md-avatar>

    <div
      class="md-list-item-text"
      v-on:click="goTo(`https://www.thecocktaildb.com/drink/${cocktail.idDrink}`)"
    >
      <span>{{cocktail.strDrink}}</span>
      <p>
        <span v-for="index in 15" :key="index">
          <span v-if="cocktail[`strIngredient${index}`]">
            <span v-if="index !== 1">,</span>
            {{cocktail[`strIngredient${index}`]}}
          </span>
        </span>
      </p>
    </div>
    <md-button class="md-icon-button md-list-action" v-on:click="deleteCocktail(idx)">
      <md-icon class="md-primary">
        <Icon name="times" scale="1.5" />
      </md-icon>
    </md-button>
  </md-list-item>
</template>

<script>
import "vue-awesome/icons//times";
import Icon from "vue-awesome/components/Icon";

export default {
  name: "LikeListItem",
  props: ["cocktail", "deleteCocktail", "idx"],
  components: {
    Icon
  },
  methods: {
    goTo: function(url) {
      window.open(url);
    }
  }
};
</script>

<style lang="scss" scoped>
.md-list-item-text {
  cursor: pointer;
  &:hover {
    background-color: rgba(0, 0, 0, 0.1);
  }
}
</style>
