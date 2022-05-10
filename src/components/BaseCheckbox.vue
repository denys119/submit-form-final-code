<template>
  <div id="checkbox-container">
    <input 
      type="checkbox"
      :checked="modelValue"
      @change="$emit('update:modelValue',$event.target.checked)"
    />
    <label>{{ label }}</label>
    <slot name="error" />
  </div>
</template>

<script>
  export default {
    name: 'BaseCheckbox',
    props: {
      modelValue: Boolean,
      label: String,
    },
    emits: ['update:modelValue'],
  }
</script>

<style scoped>
  #checkbox-container{
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    margin: 20px;
  }

  input {
    transform: scale(2);
    padding: 10px;
    cursor: pointer;
    margin-right: 10px;
  }
</style>