option = {
  title: {
    text: 'Stacked Line'
  },
  tooltip: {
    trigger: 'axis',
    // formatter: '{b0}: {c0}<br />{b1}: {c1}'
    padding: [
        10,  // 上
        10, // 右
        10,  // 下
        10, // 左
    ],      
    textStyle:{lineHeight: 56},
     formatter: '策略执行前: {c0}kW.h<br />策略执行后: {c1}kW.h<br />累计节省：64kW.h<br/>节省电费：51.20元'
  },
  grid: {
    left: '3%',
    right: '4%',
    bottom: '3%',
    containLabel: true
  },
  toolbox: {
    feature: {
      saveAsImage: {}
    }
  },
  xAxis: {
    type: 'category',
    boundaryGap: false,
    data: ["1", "2", "3", "4", "5", "6", "7"],
  },
  yAxis: {
        type: "value",
        name: "度  (kW.h)",
        min: 0,
        max: 1500,
        position: "left",
  },
  series: [
      {
      name: '执行策略后',
      type: 'line',
       data: [820, 932, 901, 934, 1290, 1330, 1320],
        label: {
        show: true,
        position: 'top'
      },
        areaStyle: {
        color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [
          {
            offset: 0,
            color: 'rgb(228,57,97)'
          },
          {
            offset: 1,
            color: 'rgb(255,150,154,0.3)',
          }
        ])
      },
    },
    {
      name: '执行策略前',
      type: 'line',
     data: [820, 932, 901, 800, 780, 771, 719],
      label: {
        show: true,
        position: 'top'
      },
      areaStyle: {
        color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [
          {
            offset: 0,
            color: 'rgb(187,233,166)',
          },
        ])
      },
    }
  ]
   
  
};