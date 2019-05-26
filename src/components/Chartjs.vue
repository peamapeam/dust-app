<template>
  <div>
    <h4>{{ station.dustboy_name}}</h4>
    <div id="box">
      <canvas
        id="myChart"
        width="400"
        height="400"
      ></canvas>
    </div>

  </div>
</template>
<script>
import Chart from "chart.js";
import Axios from "axios";
export default {
  props: ["id"],

  name: "Chartjs",

  data() {
    return {
      station: [],
      valChart: [],
      pm10: []
    };
  },
  methods: {
    getStation() {
      Axios.get(
        "https://agile-reaches-83574.herokuapp.com/api/stations/9/avghr"
      ).then(res => {
        console.log(res.data);
        this.station = res.data[0]
        this.valChart = res.data[0].value
      });
    }

  },
  mounted() {
    this.getStation();
    var ctx = document.getElementById("myChart").getContext("2d");
    var myChart = new Chart(ctx, {
      type: "bar",
      data: {
        labels: ["Red", "Blue", "Yellow", "Green", "Purple", "Orange"],
        datasets: [
          {
            label: "# of Votes",
            data: [12, 19, 3, 5, 2, 3],
            backgroundColor: "rgba(255, 99, 132, 0.2)",

            borderColor: "rgba(255, 99, 132, 1)",

            borderWidth: 1
          }
        ]
      },
      options: {
        scales: {
          yAxes: [
            {
              ticks: {
                beginAtZero: true
              }
            }
          ]
        }
      }
    });
  }
};
</script>
<style>
#box {
  width: 500px;
}
</style>

