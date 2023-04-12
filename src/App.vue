<template>
  <TheHeader
    title="Remember Me"
  ></TheHeader>
  <TheResource></TheResource>
  <!-- <StoredResource></StoredResource> -->
 
</template>

  
<script>
import TheHeader from './components/layouts/TheHeader.vue';
import TheResource from './components/Resources/TheResource.vue';
// import StoredResource from './components/Resources/StoredResource.vue';

export default {
  name: 'App',
  components: {
    TheHeader,
    TheResource,
    // StoredResource,
  },
 
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
