<template>
  <VueApexCharts type="heatmap" height="350" :options="options" :series="series" />
</template>

<script>
import VueApexCharts from "vue-apexcharts";
export default {
  components: {
    VueApexCharts
  },
  mounted() {
    this.generateData(18, { min: 0, max: 90 });
  },
  data: function() {
    return {
      options: {
        chart: {
          id: "vuechart-example"
        },
        xaxis: {
          categories: [1991, 1992, 1993, 1994, 1995, 1996, 1997, 1998]
        },
        plotOptions: {
          heatmap: {
            distributed: true
          }
        }
      },
      series: [
        {
          name: "월",
          data: [30, 40, 45, 50, 49, 60, 70, 91]
        },
        {
          name: "화",
          data: [30, 40, 45, 50, 49, 60, 70, 91]
        },
        {
          name: "수",
          data: [30, 40, 45, 50, 49, 60, 70, 91]
        },
        {
          name: "목",
          data: [30, 40, 45, 50, 49, 60, 70, 91]
        },
        {
          name: "금",
          data: [30, 40, 45, 50, 49, 60, 70, 91]
        },
        {
          name: "토",
          data: [30, 40, 45, 50, 49, 60, 70, 91]
        },
        {
          name: "일",
          data: [30, 40, 45, 50, 49, 60, 70, 91]
        }
      ]
    };
  },
  methods: {
    generateData: function(count, yrange) {
      var i = 0;
      var series = [];
      while (i < count) {
        var x = "w" + (i + 1).toString();
        var y =
          Math.floor(Math.random() * (yrange.max - yrange.min + 1)) +
          yrange.min;

        series.push({
          x: x,
          y: y
        });
        i++;
      }
      return series;
    }
  }
};
</script>

<style>
</style>
