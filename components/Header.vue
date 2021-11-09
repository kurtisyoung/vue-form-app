<template>
  <div class="header">
    <Logo />
  </div>
</template>

<style lang="scss" scoped>
.header {
  position: absolute;
  width: 100%;
  top: 0;
  left: 0;
  height: 87px;
  background: #fff;
  box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.1);
  display: flex;
  justify-content: center;
  align-items: center;
  @media only screen and (min-width: 768px) {
    box-shadow: none;
    justify-content: flex-start;
  }
}
</style>