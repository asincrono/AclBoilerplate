<template>
  <!-- Don't drop "q-app" class -->
  <div id="q-app">
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: 'app'
}
</script>

<style>

#q-app{
background-attachment:fixed;
-webkit-background-size: 100%;
-moz-background-size: 100%;
-o-background-size: 100%;
background-size: 100%;
-webkit-background-size: cover;
-moz-background-size: cover;
-o-background-size: cover;
background-size: cover;
height: 100%;
}
</style>
