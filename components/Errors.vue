<template>
  <p class="errors">
    <span>Please correct the following error(s):</span>
    <ul>
      <li v-for="error in errors" :key="error" style="">{{ error }}</li>
    </ul>
  </p>
</template>

<script>
export default {
  props: {
    errors: []
  }
}
</script>

<style lang="scss" scoped>
.errors {
  color: red;
  padding: 20px 30px;
  margin: 10px 0 15px;
  background: rgb(252, 231, 234);
  border-radius: 4px;
  span {
    font-weight: 600; 
    font-size: 14px;
  }
  li {
    font-size: 12px;
  }
}
</style>