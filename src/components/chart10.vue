<template>
  <div ref="divRef" class="chart" ></div>
</template>

<script>
import {onMounted, ref, watch} from "vue";
import * as echarts from "echarts";
import {px} from "../assets/px.js";
import {createEchartsOptions} from "../assets/create-echarts-options.js";

export default {
  setup() {
    const divRef = ref(null);
    let myChart = null;
    const data = ref([40, 22, 20, 18, 32]);

    onMounted(() => {
      myChart = echarts.init(divRef.value)
      myChart.setOption(createEchartsOptions({
        xAxis: {
          data: ['入室抢劫', '当街偷盗', '团伙诈骗', '刑事案件', '民事案件'],
          axisTick: {show: false},
          axisLine: {
            lineStyle: {color: '#083B70'}
          },
          axisLabel: {
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
        yAxis: {
          splitLine: {show: false},
          axisLine: {
            show: true,
            lineStyle: {color: '#083B70'}
          }
        },
        series: [{
          type: 'bar',
          data: data.value,
          color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [{
            offset: 0,
            color: '#0A97FB'
          }, {
            offset: 1,
            color: '#1E34FA'
          }]),
        }]
      }))
    });

    setInterval(() => {
      data.value = [Math.random() * 40, Math.random() * 40, Math.random() * 40, Math.random() * 40, Math.random() * 40]
      myChart.setOption({
        series: [{
          data: data.value
        }]
      })
    }, 2000);

    return {divRef, data}
  }
}
</script>

<style lang="scss" scoped>
.chart {
  display: flex;
  flex: 1;
}
</style>
