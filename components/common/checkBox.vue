<template>
  <label class="label">
    <input
      :name="name"
      :value="value"
      :type="inputType"
      class="input"
      :checked="current === value? true : false"
      @input="$emit('changeCheck', $event.target.value)"
    >
    <span class="text">
      {{ text }}
    </span>
  </label>
</template>
<script>
export default {
  props: ['name', 'value', 'inputType', 'current', 'text'],
  emits: ['changeCheck']
}
</script>
<style lang="scss" scope>
.label {
  position: relative;
  z-index: 2;
}

.input {
  position: absolute;
  z-index: -1;
  opacity: 0;
  margin: 10px 0 0 7px;
}

.text {
  position: relative;
  padding: 0 0 0 35px;
  font-family: "Intro Book", sans-serif;
  font-style: normal;
  font-weight: normal;
  font-size: 16px;
  line-height: 16px;
  color: #444b58;
  cursor: pointer;

  &::before {
    content: '';
    position: absolute;
    top: -2px;
    left: 0;
    width: 24px;
    height: 24px;
    border: 1px solid #cdd1da;
    border-radius: 3px;
    background: #fff;
  }

  &::after {
    content: '';
    position: absolute;
    top: -2px;
    left: 0;
    width: 24px;
    height: 24px;
    border-radius: 3px;
    background: transparent;
    box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.5);
    background-image: url("/images/icons/checked.svg");
    background-repeat: no-repeat;
    background-position: center;
    opacity: 0;
    transition: 0.2s;
  }
}

.input:checked + .text::after {
  opacity: 1;
}

.input:focus + .text::before {
  box-shadow: 0 0 0 3px rgba(186, 214, 241, 0.363);
}
</style>
