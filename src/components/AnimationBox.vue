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
  transform: rotate(90deg);
}
.left {
  z-index: 99;
  transform: rotate(-90deg);
}
#animated-box {
  width: 100%;
  transition: transform 0.5s;
  transform-origin: 50% 400%;
  position: absolute;
}
</style>
