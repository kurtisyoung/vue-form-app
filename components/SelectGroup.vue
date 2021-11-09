<template>
  <div class="select-group">
    <Label :forLabel="selectId" :label="label" />
    <v-select v-model="selected" ref="dropdown" :inputId="selectId" :placeholder="placeholder" :options="options" @input="onChange" />
  </div>
</template>

<script>
import vSelect from "vue-select";
import "vue-select/dist/vue-select.css";

export default {
  components: {
    vSelect
  },
  data() {
    return {
      selected: ""
    }
  },
  props: {
    selectId: String,
    label: String,
    placeholder: String,
    options: []
  },
  methods: {
    onChange(val) {
      this.$emit("input", val)
      this.$refs.dropdown.$el.querySelector('.vs__dropdown-toggle').style.borderColor = '#899298';
    }
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