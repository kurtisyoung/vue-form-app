<template>
  <div class="tab flex flex-column" v-show="isActive"><slot></slot></div>
</template>

<script>
export default {
  props: {
    selected: { default: false}
  },
  data(){
    return{
      isActive: false
    }
  },
  created(){
    this.isActive = this.selected
  }
}
</script>