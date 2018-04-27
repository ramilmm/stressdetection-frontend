<template>
  <line-chart v-if="mydata" :chart-data="mydata" :height="100" :width="400"/>
</template>

<script>
  import LineChart from './LineChart.vue'

   export default {
     components: {LineChart},     
     data: () => ({
       mydata: null,
      }),
      created () {
       this.mydata =  {
          labels: ['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December'],
          datasets: [
            {
              label: 'HR',
              backgroundColor: '#f87979',
              data: [60, 70, 80, 90, 100, 110, 120, 130, 140, 150, 160, 170, 180, 190, 200]
            }
          ]
        }
      }
   }
</script>