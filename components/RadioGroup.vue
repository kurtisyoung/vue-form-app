<template>
  <div class="radio-group flex flex-column">
    <p>{{ message }}</p>
    <label v-for="radio in radioList" :key="radio" :for="radio" class="radio-input">
      {{ radio }}
      <input :name="name" :id="radio" type="radio" :value="radio" @input="onChange"/>
      <span ref="radiobox" class="checkmark"/>
    </label>
  </div>
</template>

<script>
export default {
  props: {
    name: String,
    message: String,
    radioList: []
  },
  methods: {
    onChange() {
      this.$refs.radiobox[0].style.borderColor = '#008980';
      this.$refs.radiobox[1].style.borderColor = '#008980';
    }
  }
}
</script>

<style lang="scss" scoped>
.radio-group {
  margin-top: 28px;
}
p {
  font-weight: 600;
  font-size: 14px;
  line-height: 17px;
  margin-bottom: 20px;
}

.radio-input {
  display: block;
  position: relative;
  padding-left: 25px;
  margin-bottom: 12px;
  cursor: pointer;
  font-size: 16px;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

.radio-input input {
  position: absolute;
  opacity: 0;
  cursor: pointer;
  height: 0;
  width: 0;
}

.checkmark {
  position: absolute;
  top: 3px;
  left: 0;
  height: 16px;
  width: 16px;
  border-radius: 50%;
  border: 1px solid #008980;
}

.radio-input:hover input ~ .checkmark {
  background-color: #cccccc;
  opacity: 0.8;
}

.checkmark:after {
  content: "";
  position: absolute;
  display: none;
}

.radio-input input:checked ~ .checkmark:after {
  display: block;
}

.radio-input .checkmark:after {
  top: 3px;
  left: 3px;
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: #008980;
}
</style>