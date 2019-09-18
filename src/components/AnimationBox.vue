<template>
  <div v-bind:class="animation" id="animated-box" >
    <slot></slot>
  </div>
</template>



<script>

export default {
  name: "AnimationBox",
  props: ["animation"]
};
</script>

<style lang="scss" scoped>
.right {
  z-index: 99;
  transform: rotate(50deg);
}
.left {
  z-index: 99;
  transform: rotate(-50deg);
}
#animated-box {
  width: 100%;
  transition: transform 0.3s;
  transform-origin: 50% 400%;
  position: absolute;
  top: 0;

  &:last-of-type {
    position: relative;
  }
}
</style>
