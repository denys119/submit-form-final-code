<template>
  <div>
    <slot name="title" />
    <input type="text" :placeholder="placeholder" @input="$emit('update:modelValue', $event.target.value)" />
    <slot name="error" />
  </div>
</template>

<script>
  export default {
    name: 'BaseInput',
    props: {
      modelValue: String,
      placeholder: String,
    },
    emits: ['update:modelValue'],
  }
</script>

<style scoped>
  input {
    height: 40px;
    padding: 0 10px;
    font-size: 20px;
    border-radius: 10px;
    outline: none;
    border: none;
  }
</style>