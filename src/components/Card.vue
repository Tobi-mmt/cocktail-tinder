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
            {{cocktail[`strIngredient${index}`]}}
          </span>
        </span>
      </div>
    </md-card-header>

    <md-card-expand>
      <md-card-expand-content>
        <md-card-content>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Optio itaque ea, nostrum odio. Dolores, sed accusantium quasi non, voluptas eius illo quas, saepe voluptate pariatur in deleniti minus sint. Excepturi.</md-card-content>
      </md-card-expand-content>
    </md-card-expand>
  </md-card>
</template>



<script>
export default {
  name: "Card",
  props: ["cocktail"]
};
</script>

<style lang="scss" scoped>
.md-card {
  background-color: white;
  width: 90%;
  max-width: 800px;
  margin: 4px;
  display: inline-block;
  vertical-align: top;
}
</style>
