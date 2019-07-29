<template>
  <section class="hero">
    <!-- <div class="hero-body">
      <div class="container">
        <h1>Creating Beautiful Charts Using Vue.js Wrappers For Chart.js</h1>
        <h2>
          Read the article on SitePoint:
          <a
            href="https://www.sitepoint.com/creating-beautiful-charts-vue-chart-js/"
          >https://www.sitepoint.com/creating-beautiful-charts-vue-chart-js/</a>
        </h2>
        <h3>
          Download the repo from GitHub:
          <a
            href="https://github.com/sitepoint-editors/vue-charts"
          >https://github.com/sitepoint-editors/vue-charts</a>
        </h3>
      </div>
    <div>-->
    <Apexchart :options="options" :series="series"></Apexchart>
    <HeatmapChart :options="options" :series="series"></HeatmapChart>
    <ApexBarChart :options="options" :series="series"></ApexBarChart>
    <ApexLineChart></ApexLineChart>
    <Github></Github>
  </section>
</template>

<script>
import Apexchart from "../components/Apexchart";
import HeatmapChart from "../components/HeatmapChart";
import ApexBarChart from "../components/ApexBarChart";
import ApexLineChart from "../components/ApexLineChart";
import Github from "../components/Github";
export default {
  name: "home",
  components: {
    Apexchart,
    ApexBarChart,
    HeatmapChart,
    ApexLineChart,
    Github
  }
};
</script>
