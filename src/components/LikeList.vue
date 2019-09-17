<template>
  <div class="wrapper">
    <md-list>
      <div v-for="(cocktail, idx) in cocktails" v-bind:key="cocktail.idDrink">
        <LikeListItem :cocktail="cocktail" :deleteCocktail="deleteCocktail" :idx="idx" />
      </div>
    </md-list>
  </div>
</template>

<script>
import LikeListItem from "./LikeListItem";

export default {
  name: "LikeList",
  props: ["cocktails", "deleteCocktail"],
  components: {
    LikeListItem
  }
};
</script>

<style lang="scss" scoped>
.wrapper {
  max-width: 800px;
  margin: 0 auto;
}
</style>
