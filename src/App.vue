<template>
  <Navigation />
  <div class="column">
    <div class="columns">
      <router-view />
    </div>
  </div>
</template>

<script>
import Navigation from './components/Navigation.vue';

export default {
  name: 'App',
  components: { Navigation },
};
</script>

<style scoped>
.column {
  background: #f1f2f2;
  height: calc(100vh - 12vh - 2px);
}
</style>
