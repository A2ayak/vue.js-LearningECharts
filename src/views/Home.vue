<template>
  <div class="home">
    <div class="line chart">
      <LineChart></LineChart>
    </div>
    <div class="heatmap chart">heatmap</div>
    <div class="pie chart">
      <Pie></Pie>
    </div>
    <div class="bar chart">
      <Bar></Bar>
    </div>
    <div class="radar chart">
      <Radar></Radar>
    </div>
    <div class="sankey chart">
      <Sankey></Sankey>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import LineChart from "../components/LineChart";
import Heatmap from "../components/Heatmap";
import Pie from "../components/Pie";
import Bar from "../components/Bar";
import Radar from "../components/Radar";
import Sankey from "../components/Sankey";

export default {
  name: 'Home',
  components: {
    LineChart,
    Heatmap,
    Pie,
    Bar,
    Radar,
    Sankey
  }
}
</script>

<style scoped lang="less">
  .home {
    margin: 10px;
    padding: 10px;
    width: 1480px;
    height: 100vh;
    border: 1px solid red;
    background-color: #999999;
    flex-wrap: wrap;
    display: flex;
    justify-content: space-between;
    font-family: Helvetica;
    .chart {
      width: 32%;
      height: 48%;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 30px;
      font-weight: bold;
    }
    .line {
      background-color: #fff;
    }
    .bar {
      background-color: #fff;
    }
    .pie {
      background-color: #fff;
    }
    .heatmap {
      background-color: #fff;
    }
    .radar {
      background-color: #fff;
    }
    .sankey {
      background-color: #fff;
    }
  }
</style>
