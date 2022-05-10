<template>
  <div>
    <slot name="title" />
    <select @change="$emit('update:modelValue', $event.target.value)" :value="modelValue">
      <option v-for="(option, index) in options" :key="index" :value="option">
        {{ option }}
      </option>
    </select>
    <slot name="error" />
  </div>
</template>

<script>
  export default {
    name: 'BaseTextarea',
    props: {
      modelValue: String,
      options: Array,
    },
    emits: ['update:modelValue'],
  }
</script>

<style scoped>
  select {
    height: 30px;
    font-size: 20px;
  }
</style>