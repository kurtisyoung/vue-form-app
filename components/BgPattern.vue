<template>
  <img class="bg-pattern" src="/assets/bg-pattern.png" alt="bg-pattern" />
</template>

<style lang="scss" scoped>
.bg-pattern {
  display: none;
  @media only screen and (min-width: 768px) {
    position: absolute;
    display: block;
    bottom: 0;
    left: 0;
    width: 100%;
    max-height: 591px;
    height: 100%;
    z-index: -1;
  }
}
</style>