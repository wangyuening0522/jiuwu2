<script lang="ts" setup>
import { getCurrentInstance, onMounted } from "vue";
const echarts =
  getCurrentInstance().appContext.config.globalProperties.$echarts;
onMounted(() => {
  let myChart = echarts.init(document.getElementById("shidu"));
  let option = {
    series: [
      {
        type: "gauge",
        startAngle: 180,
        endAngle: 0,
        center: ["50%", "75%"],
        radius: "90%",
        min: 0,
        max: 100,
        splitNumber: 8,
        axisLine: {
          // roundCap:true,
          lineStyle: {
            width: 5,
            color: [
              [0.25, "#7CFFB2"],
              [0.5, "#58D9F9"],
              [0.75, "#FDDD60"],
              [1, "#FF6E76"],
            ],
          },
        },
        pointer: {
          icon: "path://M12.8,0.7l12,40.1H0.7L12.8,0.7z",
          length: "12%",
          width: 20,
          offsetCenter: [0, "-60%"],
          itemStyle: {
            color: "auto",
          },
        },
        axisTick: {
          length: 10,
          distance: 10,
          lineStyle: {
            color: "auto",
            width: 1,
          },
        },
        splitLine: {
          length: 20,
          distance: 10,
          lineStyle: {
            color: "auto",
            width: 3,
          },
        },
        axisLabel: {
          color: "#464646",
          fontSize: 10,
          distance: -40,
          // rotate: 'tangential',
          formatter: function (value) {
            if (value === 100) {
              return "100%";
            } else if (value === 75) {
              return "75%";
            } else if (value === 50) {
              return "50%";
            } else if (value === 25) {
              return "25%";
            } else if (value === 0) {
              return "0% ";
            }
            return "";
          },
        },
        title: {
          offsetCenter: [0, "-10%"],
          fontSize: 10,
        },
        detail: {
          fontSize: 15,
          offsetCenter: [0, "-30%"],
          valueAnimation: true,
          formatter: function (value) {
            return Math.round(value) + "";
          },
          color: "inherit",
        },
        data: [
          {
            value: 25,
            name: "机房平均湿度(%)",
            fontSize: 10,
          },
        ],
      },
    ],
  };
  myChart.setOption(option);
});
</script>
<template>
  <div id="shidu">123</div>
</template>
<style lang="scss" scoped>
#shidu {
  height: 100%;
  width: 100%;
}
</style>
