<template>
    <router-view></router-view>
</template>

<script>
import Dashboard from './components/Dashboard'
import Sabr from './components/Sabr.vue'

export default {
  name: 'app',
  components: {
    Dashboard, Sabr
  }
}
</script>

<style>
</style>
