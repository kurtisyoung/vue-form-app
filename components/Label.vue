<template>
  <label :for="label || forLabel">{{label}}</label>
</template>

<script>
export default {
  props: {
    label: String,
    forLabel: String
  }
}
</script>

<style lang="scss" scoped>
label {
  font-size: 14px;
  font-style: normal;
  font-weight: 600;
  line-height: 17px;
  letter-spacing: 0px;
  text-align: left;
}
</style>