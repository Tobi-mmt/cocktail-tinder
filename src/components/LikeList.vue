<template>
  <div class="wrapper">
    <md-list>
      <md-list-item
        class="md-double-line"
        v-for="cocktail in cocktails"
        v-bind:key="cocktail.idDrink"
      >
        <md-avatar>
          <img v-bind:src="cocktail.strDrinkThumb" />
        </md-avatar>

        <div class="md-list-item-text">
          <span>{{cocktail.strDrink}}</span>
          <p>
            {{cocktail.strIngredient1}}
            <span
              v-if="cocktail.strIngredient2"
            >, {{cocktail.strIngredient2}}</span>
            <span v-if="cocktail.strIngredient3">, {{cocktail.strIngredient3}}</span>
            <span v-if="cocktail.strIngredient4">, ...</span>
          </p>
        </div>
        <md-button class="md-icon-button md-list-action" v-on:click="goTo(`https://www.thecocktaildb.com/drink/${cocktail.idDrink}`)">
          <md-icon class="md-primary">
            <Icon name="external-link-alt" scale="1.5" />
          </md-icon>
        </md-button>
      </md-list-item>
    </md-list>
  </div>
</template>

<script>
import "vue-awesome/icons/external-link-alt";
import Icon from "vue-awesome/components/Icon";

export default {
  name: "LikeList",
  props: ["cocktails"],
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
</style>
