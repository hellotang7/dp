<template>
  <div className="图2">
    <div className="chart">
      <div ref="divRef" className="main"></div>
      <div className="text">年龄段</div>
    </div>
    <div className="legend">
      <span style="background: #856BED" />10-20
      <span style="background:#F46064" />20-30
      <span style="background: #F38E1C" />30-40
      <span style="background: #1CDB7C" />40-50
      <span style="background: #33A4FA" />50-60
    </div>
  </div>
</template>

<script>
import {onMounted, ref} from "vue";
import * as echarts from "echarts";
import {px} from "../assets/px.js";
import {createEchartsOptions} from "../assets/create-echarts-options.js";

export default {
  setup() {
    const divRef = ref(null);
    onMounted(() => {
      const myChart = echarts.init(divRef.value)
      const colors = ['#856BED', '#F46064', '#F38E1C', '#1CDB7C', '#33A4FA'];
      myChart.setOption({

        color: colors,
        xAxis: {show: false},
        yAxis: {show: false},
        legend: {show: false},
        series: [
          {
            name: '访问来源',
            type: 'pie',
            radius: ['70%', '90%'],
            avoidLabelOverlap: false,
            label: {
              show: true, position: 'inside', textStyle: {color: 'white', fontSize: px(20)},
              formatter(options) {
                return (options.value * 100).toFixed(0) + '%';
              }
            },
            labelLine: {show: false},
            itemStyle: {
              borderColor: '#0F113A',
              borderWidth: px(4)
            },
            data: [
              {value: 0.07, name: '10-20'},
              {value: 0.10, name: '20-30'},
              {value: 0.23, name: '30-40'},
              {value: 0.28, name: '40-50'},
              {value: 0.32, name: '50-60'},

            ]
          }
        ]

      })


      setInterval(()=>{
        myChart.clear()
        myChart.setOption({

          color: colors,
          xAxis: {show: false},
          yAxis: {show: false},
          legend: {show: false},
          series: [
            {
              name: '访问来源',
              type: 'pie',
              radius: ['70%', '90%'],
              avoidLabelOverlap: false,
              label: {
                show: true, position: 'inside', textStyle: {color: 'white', fontSize: px(20)},
                formatter(options) {
                  return (options.value * 100).toFixed(0) + '%';
                }
              },
              labelLine: {show: false},
              itemStyle: {
                borderColor: '#0F113A',
                borderWidth: px(4)
              },
              data: [
                {value: 0.07, name: '10-20'},
                {value: 0.10, name: '20-30'},
                {value: 0.23, name: '30-40'},
                {value: 0.28, name: '40-50'},
                {value: 0.32, name: '50-60'},

              ]
            }
          ]

        })
      },3000)

    })
    return {divRef}
  }
}
</script>

<style lang="scss" scoped>
@import "../assets/css.scss";

.图2 {

  .legend {
    flex-wrap: wrap;
  }
}
</style>
