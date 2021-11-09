<template>
  <button :type="type"><slot></slot></button>
</template>

<script>
export default {
  name: 'Button',
  props: {
    name: String,
    type: {
      type: String,
      default: 'button'
    },
  }
}
</script>

<style lang="scss" scoped>
button {
  padding: 13px 0px;
  background: #008980;
  border-radius: 4px;
  color: #fff;
  margin: 10px 0px;
}
</style>