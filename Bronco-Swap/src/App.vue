
<script setup>
import NavBar from './components/NavBar.vue'
</script>

<template>
  <div class="background">
  <NavBar class="navbar" />
  <div class="content">
    <router-view />
  </div>
  </div>
</template>

<style lang="scss" scoped>
.app {
  width: 100%;
  display: columns;
  justify-content: space-between;
}
.background {
  background-color: #f8f3ec;
  height: 1000px;
}
.navbar {
  padding: auto;
  position: sticky;
}
</style>
