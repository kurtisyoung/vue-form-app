<template>
  <label class="checkbox">
    {{ label }}
    <input :name="name" type="checkbox" @change="onChange">
    <span class="checkmark" />
  </label>
</template>

<script>
export default {
  props: ['label', 'name'],
  methods: {
    onChange(e) {
      e.target.parentElement.querySelector('.checkmark').style.borderColor = '#008980';
    }
  }
}
</script>

<style lang="scss" scoped>
.checkbox {
  display: block;
  position: relative;
  padding-left: 25px;
  margin-top: 10px;
  cursor: pointer;
  font-size: 16px;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

.checkbox input {
  position: absolute;
  opacity: 0;
  cursor: pointer;
  height: 0;
  width: 0;
}

.checkmark {
  position: absolute;
  top: 2px;
  left: 0;
  height: 18px;
  width: 18px;
  border-radius: 4px;
  border: 1px solid #008980;
}

.checkbox:hover input ~ .checkmark {
  background-color: #cccccc;
  opacity: 0.8;
}

.checkbox input:checked ~ .checkmark {
  background-color: #008980;
}

.checkmark:after {
  content: "";
  position: absolute;
  display: none;
}

.checkbox input:checked ~ .checkmark:after {
  display: block;
}

.checkbox .checkmark:after {
  left: 6px;
  top: 3px;
  width: 5px;
  height: 10px;
  border: solid white;
  border-width: 0 3px 3px 0;
  -webkit-transform: rotate(45deg);
  -ms-transform: rotate(45deg);
  transform: rotate(45deg);
}
</style>