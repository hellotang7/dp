<template>
  <div class="图2">
    <div class="chart">
      <div ref="divRef" class="main"></div>
    </div>
    <div class="legend">
      <span style="background: #856BED" />刑事
      <span style="background:#F46064" />民事
      <span style="background: #F38E1C" />经济
      <span style="background: #1CDB7C" />其他
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
    const colors = ['#F46064', '#F38E1C', '#1CDB7C', '#8D70F8', '#33A4FA'];
    onMounted(() => {
      const myChart = echarts.init(divRef.value)
      myChart.setOption(createEchartsOptions({
        color: colors,
        xAxis: {show: false},
        yAxis: {show: false},
        legend: {show: false},
        series: [
          {
            startAngle: -20,
            type: 'pie',
            radius: ['25%', '90%'],
            avoidLabelOverlap: false,
            label: {
              show: true, position: 'outside', textStyle: {color: 'white', fontSize: px(20)},
              distanceToLabelLine: 0,
              formatter(options) {
                return options.value * 100 + '%';
              }
            },
            labelLine: {show: true, length: 0},
            roseType: 'area',
            itemStyle: {
              shadowBlur: px(200),
              shadowColor: 'rgba(0, 0, 0, 0.5)'
            },
            data: [
              {value: 0.36, name: '刑事案件'},
              {value: 0.20, name: '民事案件'},
              {value: 0.18, name: '经济案件'},
              {value: 0.24, name: '其他案件'},
            ]
          }
        ]


      }))
    })
    return {divRef}
  }
}
</script>

<style lang="scss" scoped>
@import "../assets/css.scss";


</style>
