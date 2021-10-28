<template>
  <div style="height: 600px; width: 600px">
    <vue3-chart-js
      :id="doughnutChart.id"
      :type="doughnutChart.type"
      :data="doughnutChart.data"
    ></vue3-chart-js>
  </div>
</template>

<script>
import Vue3ChartJs from "@j-t-mcc/vue3-chartjs";
//create the data
//also, this will be the step where you'll get your data from a database
const stars = [135850, 52122, 148825, 16939, 9763];
const frameworks = ["React", "Angular", "Vue", "Hyperapp", "Omi"];

export default {
  name: "App",
  components: {
    Vue3ChartJs,
  },
  setup() {
    const doughnutChart = {
      id: "doughnut",
      type: "line",
      data: {
        //x axis
        //takes an array
        labels: frameworks,
        //y axis
        //takes an array object
        datasets: [
          {
            label: "Github Stars",
            //takes an array
            data: stars,
            backgroundColor: [
              "rgba(255, 99, 132, 0.2)",
              "rgba(54, 162, 235, 0.2)",
              "rgba(255, 206, 86, 0.2)",
              "rgba(75, 192, 192, 0.2)",
              "rgba(153, 102, 255, 0.2)",
            ],
            borderColor: [
              "rgba(255, 99, 132, 1)",
              "rgba(54, 162, 235, 1)",
              "rgba(255, 206, 86, 1)",
              "rgba(75, 192, 192, 1)",
              "rgba(153, 102, 255, 1)",
            ],
            borderWidth: 1,
          },
        ],
      },
      options: {
        //add this so the chart will respect our defined height
        maintainAspectRatio: false,
        //add this to force the defined width too
        responsive: false,
      },
    };

    // const beforeRenderLogic = (event) => {
    //   //...
    //   //if(a === b) {
    //   //  event.preventDefault()
    //   //}
    // };

    return {
      doughnutChart,
      // beforeRenderLogic,
    };
  },
};
</script>
