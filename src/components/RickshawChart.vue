<template>
  <div>
    <div class="container-fluid">
      <div class="row text-center">
        <div class="col-xs-12 col-lg-4 col-lg-offset-4">
        </div>

        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3 col-lg-4 col-lg-offset-4">

          <!-- Panel div start -->
          <div class="panel panel-primary">
            <div class="panel-body">
              <!-- Chart container -->
              <div id="chart_container" >
                <div id="y_axis"></div>
                <div id="demo_chart" ref="panel"></div>
              </div>
              <!-- End of chart container -->
            </div>
          </div>
          <!-- Panel div end -->
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import Rickshaw from 'rickshaw'
  import 'rickshaw/rickshaw.min.css'
  var magnitudeChart;

  export default {
    name: 'home',
    data() {
      return {
        messageSeries: [],
        updateInterval: 20,
        dvColors: {
          v1: "#cb503a",
        }
      }
    },
    mounted() {
      this.initChart();
    },
    methods: {
      /* Rickshaw.js initialization */
      initChart() {
        magnitudeChart = new Rickshaw.Graph({
          element: document.querySelector("#demo_chart"),
          width: "600",
          height: "250",
          renderer: "line",
          min: 40,
          max: 200,
          series: new Rickshaw.Series.FixedDuration([{
            name: 'v1',
            color: '#EC644B'
          }], undefined, {
            timeInterval: this.updateInterval,
            maxDataPoints: 100,
            timeBase: new Date().getTime() / 1000

          })
        });

        var y_axis = new Rickshaw.Graph.Axis.Y({
          graph: magnitudeChart,
          orientation: 'left',
          tickFormat: function(y) {
            return y.toFixed(1);
          },
          ticks: 5,
          element: document.getElementById('y_axis'),
        });

        this.resizeChart(magnitudeChart);

        window.addEventListener('resize', () => {
          this.resizeChart(magnitudeChart)
        });

      },
      resizeChart(chart) {
        chart.configure({
          width: this.$refs.panel.clientWidth,
        });
        chart.render();
      },
      returnRandom(min, max) {
        return (Math.random() * (max - min) + min);
      },
      insertData(data) {
        let tmp = {
          one: data
        };
        magnitudeChart.series.addData(tmp);
        magnitudeChart.render();
      },
      fetchData() {
        let _this = this;
        this.$http.get('http://localhost:8081/data')
          .then(function(response) {
            _this.insertData(response.data);
          });
      },
    },
    created() {
      let _this = this;
      setInterval(function() {
        _this.fetchData();
      }, 300);
    }
  }
</script>

<style scoped>
  #chart_container {
    padding-right: 40px;
    padding-bottom: 20px;
    margin-top: 20px;
    position: relative;
  }

  #demo_chart {
    position: relative;
    left: 40px;
  }

  #y_axis {
    position: absolute;
    top: 0;
    bottom: 0;
    width: 40px;
  }

  .footy {
    position: relative;
    width: 100%;
    margin-top: 50px;
    height: 60px;
    opacity: 0.2;
  }

  .glyphicon {
    color: #8E44AD;
    font-weight: bold;
  }
</style>
