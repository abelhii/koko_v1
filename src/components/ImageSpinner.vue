<template>
  <div class="ripple">
    <div class="ripple__circle"></div>
    <div class="ripple__circle ripple__inner-circle"></div>
  </div>
</template>

<style lang="scss" scoped>
@import "@/styles/_defaultVars.scss";

//Credits: https://css-tricks.com/lazy-loading-images-with-vue-js-directives-and-intersection-observer/
.ripple {
  display: inline-block;
  position: absolute;
  width: 64px;
  height: 64px;

  &__circle {
    position: absolute;
    border: 4px solid $accent;
    opacity: 1;
    border-radius: 50%;
    animation: ripple 1s cubic-bezier(0, 0.2, 0.8, 1) infinite;
  }

  &__inner-circle {
    animation-delay: -0.5s;
  }
}

@keyframes ripple {
  0% {
    top: 28px;
    left: 28px;
    width: 0;
    height: 0;
    opacity: 1;
  }
  100% {
    top: -1px;
    left: -1px;
    width: 58px;
    height: 58px;
    opacity: 0;
  }
}
</style>
