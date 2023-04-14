<template>
  <div class="bordered 管辖统计">
    <h2>案发派出所管辖统计</h2>
    <div ref="divRef" class="chart"></div>
  </div>
</template>

<script>
import {onMounted, ref} from "vue";
import * as echarts from "echarts";

  const px = (n) => n /2420*pageWidth;

  export default {
    setup(){
      const divRef = ref(null);
      onMounted(() => {
        const myChart = echarts.init(divRef.value)
        myChart.setOption({
          textStyle: {
            fontSize: px(12),
            color: '#79839E'
          },
          title: {show: false},
          legend: {show: false},
          xAxis: {
            data: ['兰州新区', '兰州新区', '兰州新区', '兰州新区', '兰州新区', '兰州新区', '兰州新区', '兰州新区', '兰州新区'],
            axisTick: {show: false},
            axisLine: {
              lineStyle: {color: '#083B70'}
            },
            axisLabel: {
              margin:px(10),
              fontSize: px(12),
              formatter(val) {
                if (val.length > 2) {
                  const array = val.split('');
                  array.splice(2, 0, '\n');
                  return array.join('');
                } else {
                  return val;
                }
              }
            },

          },
          grid: {
            x: px(40),
            y: px(40),
            x2: px(35),
            y2: px(45 ),
          },
          yAxis: {

            splitLine: {show: false},
            axisLine: {
              show: true,
              lineStyle: {color: '#083B70'}

            },
            axisLabel: {
              margin:px(6),
              fontSize: px(12)
            }
          },
          series: [{
            type: 'bar',
            data: [10, 20, 36, 41, 15, 26, 37, 18, 29]
          }]

        })

      })
      return {divRef}
    },

  }



</script>

<style lang="scss" scoped>
.管辖统计 {
  height: 315/ 2420 * 100rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  h2 {
    flex-shrink: 0;
    border: 1px solid #0a5299;
    border-bottom-left-radius: 4px;
    border-bottom-right-radius: 4px;
    font-size: 22 / 2420 * 100rem;
    line-height: 24 / 2420 * 100rem;
    padding: 10 / 2420 * 100rem 28 / 2420 * 100rem;
    text-shadow: 0 0 3 / 2420 * 100rem white;
  }
  .chart{
    flex: 1;
    width: 100%;
  }
}
</style>
