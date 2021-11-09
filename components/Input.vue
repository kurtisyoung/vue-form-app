<template>
  <span :class="`input-field flex flex-column col-${col}`">
    <Label :label="label"/>
    <textarea 
      v-if="type === 'textarea'"
      ref="input"
      :name="name"
      :placeholder="placeholder"
    />
    <input
      v-else
      ref="input"
      :name="name"
      :type="type"
      :placeholder="placeholder"
      v-model="inputValue"
      @input="onChange"
    />
    <Checkbox v-if="confirmContent && inputChanged" name="confirmContent" label="Yes, I confirm that the content I submit is authored by me."  />
  </span>
</template>

<script>
export default {
  name: 'Input',
  data() {
    return {
      inputValue: "",
      inputChanged: false
    }
  },
  props: {
    label: String, 
    type: String,
    name: String,
    placeholder: String,
    col: {
      type: String,
      default: '6'
    },
    confirmContent: {
      type: Boolean,
      default: false
    }
  },
  methods:{
    onChange() {
      if(this.inputValue) {
        this.inputChanged = true;
        this.$refs.input.style.borderColor = '#899298';
      } else {
        this.inputChanged = false;
      }
    }
  }
}
</script>

<style lang="scss" scoped>
.input-field {
  padding: 0;
  margin: 14px 0;
}
input, textarea {
  border: 1px solid #899298;
  border-radius: 4px;
  height: 40px;
  background: #FBFBFD;
  font-size: 16px;
  line-height: 22px;
  padding: 12px;
  &:focus, &:focus-visible {
    outline-color: #008980;
    outline-width: 1px;
    outline-offset: 1px;
  }
}
textarea {
  height: 87px;
  vertical-align: top;
}

</style>