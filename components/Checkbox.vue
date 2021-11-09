<template>
  <label class="checkbox">
    {{ label }}
    <input type="checkbox">
    <span class="checkmark" />
  </label>
</template>

<script>
export default {
  props: ['label']
}
</script>

<style lang="scss" scoped>
/* Customize the label (the checkbox) */
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

/* Hide the browser's default checkbox */
.checkbox input {
  position: absolute;
  opacity: 0;
  cursor: pointer;
  height: 0;
  width: 0;
}

/* Create a custom checkbox */
.checkmark {
  position: absolute;
  top: 2px;
  left: 0;
  height: 18px;
  width: 18px;
  border-radius: 4px;
  border: 1px solid #008980;
}

/* On mouse-over, add a grey background color */
.checkbox:hover input ~ .checkmark {
  background-color: #cccccc;
  opacity: 0.8;
}

/* When the checkbox is checked, add a blue background */
.checkbox input:checked ~ .checkmark {
  background-color: #008980;
}

/* Create the checkmark/indicator (hidden when not checked) */
.checkmark:after {
  content: "";
  position: absolute;
  display: none;
}

/* Show the checkmark when checked */
.checkbox input:checked ~ .checkmark:after {
  display: block;
}

/* Style the checkmark/indicator */
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