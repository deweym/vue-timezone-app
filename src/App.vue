<template>
  <div id="app">
    <Timezone />
  </div>
</template>

<script>
import Timezone from './components/Timezone.vue';

export default {
  name: 'App',
  components: {
    Timezone
  }
}
</script>

<style>
#app {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
</style>
