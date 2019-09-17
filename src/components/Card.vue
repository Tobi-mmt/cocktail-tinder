<template>
  <md-card>
    <md-card-media>
      <img v-bind:src="cocktail.strDrinkThumb" />
    </md-card-media>

    <md-card-header>
      <div class="md-title">{{cocktail.strDrink}}</div>
      <div class="md-subhead">
        <span v-for="index in 15" :key="index">
          <span v-if="cocktail[`strIngredient${index}`]">
            <span v-if="index !== 1">,</span>
            {{cocktail[`strMeasure${index}`]}} {{cocktail[`strIngredient${index}`]}}
          </span>
        </span>
      </div>
    </md-card-header>

    <md-card-actions md-alignment="space-between">
      <md-card-expand-trigger>
        <md-button class="md-icon-button">
          <Icon name="chevron-down" />
        </md-button>
      </md-card-expand-trigger>
    </md-card-actions>

    <md-card-expand>
      <md-card-expand-content>
        <md-card-content>{{cocktail.strInstructions}}</md-card-content>
      </md-card-expand-content>
    </md-card-expand>
  </md-card>
</template>



<script>
import "vue-awesome/icons/chevron-down";
import Icon from "vue-awesome/components/Icon";

export default {
  name: "Card",
  props: ["cocktail"],
  components: {
    Icon
  }
};
</script>

<style lang="scss" scoped>
.md-button {
  line-height: 0;
  margin: auto !important;
}
.md-subhead{
  min-height: 2em;
}
.md-card {
  background-color: white;
  width: 90%;
  max-width: 800px;
  margin: 4px;
  display: inline-block;
  vertical-align: top;
}
</style>
