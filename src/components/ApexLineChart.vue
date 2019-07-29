<template>
  <apexchart type="line" height="350" :options="chartOptions" :series="series" />
</template>

<script>
import VueApexCharts from "vue-apexcharts";

export default {
  components: {
    apexchart: VueApexCharts
  },
  mounted() {
    // for (let i in this.githubIds) {
    //   this.getRepos(this.githubIds[i]);
    // }
    // this.getCommit("13akstjq/prismagram");
    // const request = new XMLHttpRequest();
    // const url = "https://github.com"; // 긁어오고 싶은 주소를 넣는다. 예제는 네이버
    // request.open("GET", url, true);
    // request.onload = function() {
    //   console.log(request.responseText); // 긁어온 내용 뿌리기
    // };
    // request.send();
    // const request = require("request");
    // const url =
    //   "http://www.inu.ac.kr/com/cop/mainWork/foodList1.do?siteId=inu&id=inu_050110010000&command=week";
    // request(url, (error, response, body) => {
    //   if (error) throw error;
    //   console.log(body);
    // });
  },
  data() {
    return {
      //   githubIds: ["13akstjq", "leeiopd", "sweetrain096", "yeonjilim", "dkyou7"],
      githubIds: ["13akstjq"],
      series: [
        {
          name: "",
          data: [28, 29, 33, 36, 32, 32, 33]
        },
        {
          name: "Low - 2013",
          data: [12, 11, 14, 18, 17, 13, 13]
        },
        {
          name: "Low - 2013",
          data: [1, 2, 7, 5, 3, 9, 6]
        }
      ],
      chartOptions: {
        chart: {
          shadow: {
            enabled: true,
            color: "#000",
            top: 18,
            left: 7,
            blur: 10,
            opacity: 1
          },
          toolbar: {
            show: false
          }
        },
        colors: ["#77B6EA", "#545454"],
        dataLabels: {
          enabled: true
        },
        stroke: {
          curve: "smooth"
        },
        title: {
          text: "Average High & Low Temperature",
          align: "left"
        },
        grid: {
          borderColor: "#e7e7e7",
          row: {
            colors: ["#f3f3f3", "transparent"], // takes an array which will be repeated on columns
            opacity: 0.5
          }
        },
        markers: {
          size: 6
        },
        xaxis: {
          categories: ["Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul"],
          title: {
            text: "Date"
          }
        },
        yaxis: {
          title: {
            text: "Commit"
          },
          min: 1,
          max: 40
        },
        legend: {
          position: "top",
          horizontalAlign: "right",
          floating: true,
          offsetY: -25,
          offsetX: -5
        }
      }
    };
  },
  methods: {
    getRepos: async function(githubId) {
      let url = `https://api.github.com/users/${githubId}/repos`;
      let response = await fetch(url);
      let results = await response.json();

      for (let i in results) {
        url = `https://api.github.com/repos/${results[i].full_name}/commits`;
        let headers = {
          Accept: "application/vnd.github.cloak-preview"
        };
        response = await fetch(url, {
          method: "GET",
          headers: headers
        });

        let result = await response.json();
        console.log(result);
      }
    }
  }
};
</script>

<style>
</style>
