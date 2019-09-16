<template>
  <div class="wrapper">
    <Icon name="heart" scale="6" style="color: red" />
    <div class="counter">
      <p>{{counter}}</p>
    </div>
  </div>
</template>

<script>
import "vue-awesome/icons/heart";
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
}
.counter {
  font-size: 2em;
  position: absolute;
  top: 1.5em;
  z-index: 555;
  width: 100%;
  p {
    color: white;
    margin: 0;
    font-weight: 600;
  }
}
</style>
