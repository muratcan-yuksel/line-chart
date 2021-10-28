<template>
  <div style="height: 600px; width: 600px">
    <vue3-chart-js
      :id="lineChart.id"
      :type="lineChart.type"
      :data="lineChart.data"
    ></vue3-chart-js>
  </div>
</template>

<script>
import Vue3ChartJs from "@j-t-mcc/vue3-chartjs";
//create the data
//also, this will be the step where you'll get your data from a database
const price = [
  59, 529.8, 61, 312.5, 60, 861.1, 54, 942.5, 47, 666.9, 42, 686.8, 48, 306.7,
  45, 161.9, 49, 918.4, 48, 897.1,
];
const date = [
  "Oct 24, 2021",
  "Oct 17, 2021",
  "Oct 10, 2021",
  "Oct 03, 2021",
  "Sep 26, 2021	",
  "Sep 19, 2021",
  "Sep 12, 2021",
  "Sep 05, 2021",
  "Aug 29, 2021",
  "Aug 22, 2021",
];

export default {
  name: "App",
  components: {
    Vue3ChartJs,
  },
  setup() {
    const lineChart = {
      id: "line",
      type: "line",
      data: {
        //x axis
        //takes an array
        labels: date,
        //y axis
        //takes an array object
        datasets: [
          {
            label: "Btc price in the last 10 weeks",
            //takes an array
            data: price,
            backgroundColor: ["yellow"],
            borderColor: ["black"],
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
      lineChart,
      // beforeRenderLogic,
    };
  },
};
</script>
