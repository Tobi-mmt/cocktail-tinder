<template>
  <div class="wrapper">
    <p class="headline">cocktail <Icon name="wine-glass" scale="6" /> lover</p>
    <div class="counter">
      <p>{{counter}}</p>
    </div>
  </div>
</template>

<script>
import "vue-awesome/icons/wine-glass";
import Icon from "vue-awesome/components/Icon";

export default {
  name: "LikeCounter",
  props: ["counter"],
  components: {
    Icon
  }
};
</script>

<style lang="scss" scoped>
.wrapper {
  cursor: pointer;
  margin-top: 1em;
}
.headline {
  font-size: 3em;
  margin: 0;
}
.counter {
  padding-left: 1.7em;
  font-size: 2em;
  position: absolute;
  top: 1.3em;
  z-index: 555;
  width: 100%;
  p {
    color: white;
    margin: 0;
    font-weight: 600;
  }
}
</style>
