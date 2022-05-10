<template>
  <div id="radio-button">
    <input 
      type="radio"
      :checked="modelValue === value"
      :value="value"
      @change="$emit('update:modelValue',$event.target.value)"
    />
    <label>{{ label }}</label>
  </div>
</template>

<script>
  export default {
    name: 'BaseRadio',
    props: {
      modelValue: String,
      label: String,
      value: String
    },
    emits: ['update:modelValue'],
  }
</script>

<style scoped>
  #radio-button {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
  }

  #radio-button input {
    width: 30px;
    height: 30px;
    cursor: pointer;
  }
</style>