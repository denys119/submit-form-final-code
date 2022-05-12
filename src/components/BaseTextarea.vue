<template>
  <div>
    <slot name="title" />
    <textarea :placeholder="placeholder" @input="$emit('update:modelValue', $event.target.value)" />
    <slot name="error" />
  </div>
</template>

<script>
  export default {
    name: 'BaseTextarea',
    props: {
      modelValue: String,
      placeholder: String,
    },
    emits: ['update:modelValue'],
  }
</script>

<style scoped>
  textarea {
    min-height: 100px;
    max-height: 100px;
    overflow: auto;
    resize: none;
    padding: 0 10px;
    font-size: 20px;
    border-radius: 10px;
    outline: none;
    border: none;
  }
</style>