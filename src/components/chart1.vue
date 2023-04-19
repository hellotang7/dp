<template>
  <div class="bordered 管辖统计">
    <h2>案发派出所管辖统计</h2>
    <div ref="divRef" class="chart"></div>
  </div>
</template>

<script>
import {onMounted, ref} from "vue";
import * as echarts from "echarts";
import {px} from "../assets/px.js";
import {createEchartsOptions} from "../assets/create-echarts-options.js";
  export default {
    setup(){
      const divRef = ref(null);
      let myChart =null
      const data = ref([10, 20, 36, 41, 15, 26, 37, 18, 29])

      onMounted(() => {
        myChart = echarts.init(divRef.value)
        myChart.setOption(createEchartsOptions({
          xAxis: {
            data: ['浙江省', '安徽省', '江苏省', '山东省', '河南省', '陕西省', '河北省', '云南省', '贵州省'],
            axisTick: {show: false},
            axisLine: {
              lineStyle: {color: '#083B70'}
            },
            axisLabel: {
              margin:px(10),
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
            },
            axisLabel: {
              margin:px(6),

            }
          },
          series: [{
            type: 'bar',
            data: data.value
          }]

        }))
      });


      setInterval(() => {
        data.value = data.value.map(item => item + Math.floor(Math.random() * 10) + 1)
        myChart.setOption({
          series: [{
            data: data.value
          }]
        })
      }, 1000);

      return {divRef, data}


    },

  }



</script>

<style lang="scss" scoped>
@import "../assets/css.scss";


</style>
