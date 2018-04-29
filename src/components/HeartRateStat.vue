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
              backgroundColor: '#f84b53',
              data: [71,121,121,164,140,90,91,204, 147,113,150,177,107,132,86,180,152,96,142,104,96,150,158,120,152,167,108,69,78,129,140,101,76,68,124,132,118,78,68,149,132,89,128,170,124,142,179,134,134,118,168,74,105,143,119,143,158,70,95,76,178,102,113,109,87,172,132,114,138,171,135,100,109,172,169,65,166,79,65,157,134,108,161,116,161,161]
            }
          ]
        }
      }
   }
</script>
