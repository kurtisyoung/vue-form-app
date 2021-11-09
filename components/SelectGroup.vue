<template>
  <div class="select-group">
    <Label :forLabel="selectId" :label="label" />
    <v-select :inputId="selectId" :placeholder="placeholder" :options="options" />
  </div>
</template>

<script>
import vSelect from "vue-select";
import "vue-select/dist/vue-select.css";

export default {
  components: {
    vSelect
  },
  props: {
    selectId: String,
    label: String,
    placeholder: String,
    options: []
  }
}
</script>

<style lang="scss">
.select-group {
  margin: 14px 0;
}
.vs__dropdown-toggle {
  border-color: #899298;
  padding: 5px;
  border-radius: 4px;
  background: #FBFBFD;
}
.vs__dropdown-option--highlight {
  background: #F4F8FB !important;
  color: #303538;
}
.vs__dropdown-option {
  padding: 7px 20px;
}
::placeholder {
  color: #6E777D !important;
}
</style>