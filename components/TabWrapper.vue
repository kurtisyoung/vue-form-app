<template>
  <div class="tab-wrapper flex flex-column">
    <div class="tab-counter">Step {{ currentActive + 1 }} of {{ totalTabs }} </div>
    <div class="tab-details">
        <slot></slot>
    </div>
    <div class="tab-buttons flex">
      <Button
        class="next-btn col-12"
        @click.native.prevent="changeTab(currentActive++)" v-if="currentActive < totalTabs - 1"
      >
        Next
      </Button>
      <span class="back-span col-12 col-md-6"
        @click="changeTab(currentActive--)" v-if="currentActive > 0"
      >
        &#60; Back
      </span>
      <Button 
        v-if="currentActive == totalTabs -1" 
        class="submit-btn col-12 col-md-6"
        type="submit"
      >
        Submit Application
      </Button>
    </div>
  </div>
</template>

<script>
export default {
  data(){
    return {
      tabs: [],
      currentActive: 0,
      totalTabs: 0,
    }
  },
  created(){
    this.tabs = this.$children;
  },
  mounted(){
    this.totalTabs = this.tabs.length;
  },
  methods:{
    changeTab(){
      this.tabs.forEach(tab => {
        tab.isActive = false;
      });
      this.tabs[this.currentActive].isActive = true;
    }
  }
}
</script>

<style lang="scss" scoped>
.tab-counter {
  position: absolute;
  top: 1.5rem;
  right: 1.5rem;
  font-weight: 600;
  font-size: 12px;
  line-height: 12px;
  letter-spacing: 0.25px;
  text-transform: uppercase;
}
.tab-buttons {
  flex-direction: column;
  margin-top: 10px;
  justify-content: flex-end;
  @media only screen and (min-width: 768px) {
    flex-direction: row;
  }
}
.next-btn {
  @media only screen and (min-width: 768px) {
    max-width: 152px;
  }
}
.back-span {
  cursor: pointer;
  font-weight: 600;
  font-size: 18px;
  line-height: 22px;
  color: #088178;
  order: 1;
  text-align: center;
  margin-top: 14px;
  padding: 0;
  @media only screen and (min-width: 768px) {
    order: 0;
    margin-top: 0;
    text-align: left;
    display: flex;
    justify-self: center;
    align-items: center;
  }
}
</style>