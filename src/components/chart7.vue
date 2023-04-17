<template>
  <div class="图1">
    <div class="chart">
      <div ref="divRef" class="main"></div>
      <div class="text">性别</div>
    </div>
    <div class="legend">
      <span class="male"/>男
      <span class="female"/>女
    </div>
  </div>
</template>

<script>
import {onMounted, ref} from "vue";
import * as echarts from "echarts";
import {px} from "../assets/px.js";

export default {
  setup() {
    const divRef = ref(null);
    onMounted(() => {
      const myChart = echarts.init(divRef.value)
      myChart.setOption({

        color: ['#8D70F8', '#33A4FA'],
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
                return options.value * 100 + '%';
              }
            },
            labelLine: {show: false},
            itemStyle: {
              borderColor: '#0F113A',
              borderWidth: px(4)
            },
            data: [
              {value: 0.2, name: '女'},
              {value: 0.8, name: '男'},
            ]
          }
        ]

      })
    })
    return {divRef}
  }
}
</script>

<style lang="scss" scoped>
@import "../assets/css.scss";
</style>
