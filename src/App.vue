<template>
    <router-view></router-view>
</template>

<script>
import Dashboard from './components/Dashboard'
import GSR from './components/GSR.vue'

export default {
  name: 'app',
  components: {
    Dashboard, GSR
  }
}
</script>

<style>
</style>
