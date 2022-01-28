<template>
  <div style="height: 400px; width: 500px">
    <vue-echarts :option="option" />
  </div>
</template>

<script>
import VueEcharts from "vue-echarts";
import { use } from "echarts/core";

import { CanvasRenderer } from "echarts/renderers";
import {
  BarChart,
  LineChart,
  PieChart,
  PictorialBarChart,
} from "echarts/charts";
import {
  GridComponent,
  TooltipComponent,
  LegendComponent,
  TitleComponent,
  ToolboxComponent,
  DataZoomComponent,
  MarkLineComponent,
  MarkPointComponent,
  LegendScrollComponent,
} from "echarts/components";

use([
  CanvasRenderer,
  BarChart,
  LineChart,
  PieChart,
  GridComponent,
  TooltipComponent,
  LegendComponent,
  TitleComponent,
  ToolboxComponent,
  DataZoomComponent,
  MarkLineComponent,
  MarkPointComponent,
  LegendScrollComponent,
  PictorialBarChart,
]);
export default {
  components: {
    VueEcharts,
  },
  data() {
    return {
      option: {
        tooltip: {
          trigger: "axis",
          axisPointer: {
            type: "cross",
            label: {
              backgroundColor: "#6a7985",
            },
          },
        },
        title:{
          text: "快速模式"
        },
        xAxis: {
          type: "category",
          data: [1,2,3,4,5],
        },
        yAxis: {
          type: "value",
        },
        series: [
          {
            data: [2,3,4,5,6],
            type: "bar",
            label: {
              show: true
            }
          },
        ],
      },
    };
  },
};
</script>

<style>
</style>