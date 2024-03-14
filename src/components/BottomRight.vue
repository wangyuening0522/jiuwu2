<script setup lang="ts">
import { getCurrentInstance, onMounted } from "vue";
const echarts =
  getCurrentInstance().appContext.config.globalProperties.$echarts;
onMounted(() => {
  // 基于准备好的dom，初始化echarts实例
  let myChart = echarts.init(document.getElementById("myChart"));
  // 绘制图表
  myChart.setOption({
    title: {
      text: "空调22执行定时调温策略2",
    },
    grid: {
      left: "3%",
      right: "4%",
      bottom: "3%",
      containLabel: true,
    },
    toolbox: {
      feature: {
        saveAsImage: {},
      },
    },
    tooltip: {
      trigger: "axis",
      // formatter: '{b0}: {c0}<br />{b1}: {c1}'
      padding: [
        10, // 上
        10, // 右
        10, // 下
        10, // 左
      ],
      textStyle: { lineHeight: 56 },
      formatter:
        "策略执行前: {c0}kW.h<br />策略执行后: {c1}kW.h<br />累计节省：64kW.h<br/>节省电费：51.20元",
    },
    tooltip: {
      trigger: "axis",
      axisPointer: {
        type: "cross",
        label: {
          backgroundColor: "#6a7985",
        },
      },
    },
    xAxis: [
      {
        type: "category",
        axisTick: {
          alignWithLabel: true,
        },
        data: ["1", "2", "3", "4", "5", "6", "7"],
      },
    ],
    yAxis: [
      {
        type: "value",
        name: "度  (kW.h)",
        min: 0,
        max: 1500,
        position: "left",
      },
    ],
    series: [
      {
        name: "执行策略后",
        type: "line",
        data: [820, 932, 901, 934, 1290, 1330, 1320],
        label: {
          show: true,
          position: "top",
        },
        areaStyle: {
          color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [
            {
              offset: 0,
              color: "rgb(228,57,97)",
            },
            {
              offset: 1,
              color: "rgb(255,150,154,0.3)",
            },
          ]),
        },
      },
      {
        name: "执行策略前",
        type: "line",
        data: [820, 932, 901, 800, 780, 771, 719],
        label: {
          show: true,
          position: "top",
        },
        areaStyle: {
          color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [
            {
              offset: 0,
              color: "rgb(187,233,166)",
            },
          ]),
        },
      },
    ],
  });
});
</script>
<template>
  <div class="BottomRight">
    <div id="myChart"></div>
  </div>
</template>
<style lang="scss" scoped>
#myChart {
  height: 400px;
  width: 700px;
}
</style>
