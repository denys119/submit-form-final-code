<template>
  <div id="main">
    <simple-form />
  </div>
</template>

<script>
import SimpleForm from './components/SimpleForm.vue';
export default {
  name: 'App',
  components: {
    SimpleForm,
  },
}
</script>

<style scoped>
@import './assets/css/default.css';
#main {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
}
</style>
