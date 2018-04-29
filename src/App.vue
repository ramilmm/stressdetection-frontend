<template>
    <router-view></router-view>
</template>

<script>
import Dashboard from './components/Dashboard'
import GSRChart from './components/charts/GSRChart.vue'
import HRChart from './components/charts/HRChart.vue'
import StressChart from './components/charts/StressChart.vue'

export default {
  name: 'app',
  components: {
    Dashboard, GSRChart, HRChart, StressChart
  }
}
</script>

<style>
</style>
