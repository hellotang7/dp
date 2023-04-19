<template>
  <div class="bordered 趋势分析">
    <h2>案件破获排名</h2>
    <div ref="divRef" class="chart"></div>
  </div>
</template>

<script>
import {createEchartsOptions} from "../assets/create-echarts-options.js";
import {px} from "../assets/px.js";
import {onMounted, ref} from "vue";
import * as echarts from "echarts";

export default {
  setup() {
    const divRef = ref(null);
    onMounted(() => {
      const myChart = echarts.init(divRef.value)
      myChart.setOption(createEchartsOptions({
        legend: {
          bottom: px(10),
          textStyle: {color: 'white'},
          itemWidth: px(30),
          itemHeight: px(16)
        },
        grid: {
          x: px(20),
          x2: px(20),
          y: px(20),
          y2: px(80),
          containLabel: true
        },
        xAxis: {
          type: 'category',
          boundaryGap: false,
          data: [2010, 2011, 2012, 2013, 2014, 2015, 2016, 2017, 2018],
          splitLine: {show: true, lineStyle: {color: '#073E78'}},
          axisTick: {show: false},
          axisLine: {show: false},
        },
        yAxis: {
          type: 'value',
          splitLine: {lineStyle: {color: '#073E78'}},
          axisLabel: {
            formatter(val) {
              return val * 100 + '%';
            }
          }
        },
        series: [
          {
            name: '抢劫',
            type: 'line',
            data: [0.01, 0.02, 0.03, 0.04, 0.05, 0.06, 0.07, 0.08, 0.09].reverse()
          },
          {
            name: '醉驾',
            type: 'line',
            data: [0.03, 0.04, 0.05, 0.06, 0.07, 0.08, 0.09, 0.10, 0.11].reverse()
          },
          {
            name: '盗窃',
            type: 'line',
            data: [0.05, 0.06, 0.07, 0.08, 0.09, 0.10, 0.11, 0.12, 0.13].reverse()
          },
          {
            name: '故意杀人',
            type: 'line',
            data: [0.07, 0.08, 0.09, 0.10, 0.11, 0.12, 0.13, 0.14, 0.15].reverse()
          },
          {
            name: '故意伤人',
            type: 'line',
            data: [0.09, 0.10, 0.11, 0.12, 0.13, 0.14, 0.15, 0.16, 0.17].reverse()
          }
        ].map(obj => ({
          ...obj,
          symbol: 'circle',
          symbolSize: px(12),
          lineStyle: {width: px(2)}
        }))

      }))

      setInterval(()=>{
        myChart.clear()
        myChart.setOption(createEchartsOptions({
          legend: {
            bottom: px(10),
            textStyle: {color: 'white'},
            itemWidth: px(30),
            itemHeight: px(16)
          },
          grid: {
            x: px(20),
            x2: px(20),
            y: px(20),
            y2: px(80),
            containLabel: true
          },
          xAxis: {
            type: 'category',
            boundaryGap: false,
            data: [2010, 2011, 2012, 2013, 2014, 2015, 2016, 2017, 2018],
            splitLine: {show: true, lineStyle: {color: '#073E78'}},
            axisTick: {show: false},
            axisLine: {show: false},
          },
          yAxis: {
            type: 'value',
            splitLine: {lineStyle: {color: '#073E78'}},
            axisLabel: {
              formatter(val) {
                return val * 100 + '%';
              }
            }
          },
          series: [
            {
              name: '抢劫',
              type: 'line',
              data: [0.01, 0.02, 0.03, 0.04, 0.05, 0.06, 0.07, 0.08, 0.09].reverse()
            },
            {
              name: '醉驾',
              type: 'line',
              data: [0.03, 0.04, 0.05, 0.06, 0.07, 0.08, 0.09, 0.10, 0.11].reverse()
            },
            {
              name: '盗窃',
              type: 'line',
              data: [0.05, 0.06, 0.07, 0.08, 0.09, 0.10, 0.11, 0.12, 0.13].reverse()
            },
            {
              name: '故意杀人',
              type: 'line',
              data: [0.07, 0.08, 0.09, 0.10, 0.11, 0.12, 0.13, 0.14, 0.15].reverse()
            },
            {
              name: '故意伤人',
              type: 'line',
              data: [0.09, 0.10, 0.11, 0.12, 0.13, 0.14, 0.15, 0.16, 0.17].reverse()
            }
          ].map(obj => ({
            ...obj,
            symbol: 'circle',
            symbolSize: px(12),
            lineStyle: {width: px(2)}
          }))

        }))      },3000)

    })
    return {divRef}
  }
}
</script>

<style lang="scss" scoped>
 @import "../assets/css.scss";
 .趋势分析{
   height: 363/ 2420 * 100rem;

 }
</style>
