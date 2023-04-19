<template>
  <div class="bordered 时段分析">
    <h2>案发时段分析</h2>
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
    const myChart = ref(null)
    const data = [
      {name: '0', 2011:  0.15},
      {name: '2', 2011: 0.13},
      {name: '4', 2011:  0.11},
      {name: '6', 2011:0.13},
      {name: '8', 2011: 0.14},
      {name: '10', 2011:0.15},
      {name: '12', 2011: 0.16},
      {name: '14', 2011:0.18},
      {name: '16', 2011: 0.21},
      {name: '18', 2011: 0.19},
      {name: '20', 2011: 0.17},
      {name: '22', 2011: 0.16},
      {name: '24', 2011: 0.15},
    ]
onMounted(()=>{
  setInterval(()=>{
    const newData = [
      {name: '0', 2011:  Math.random() / 10},
      {name: '2', 2011: Math.random() / 10},
      {name: '4', 2011:  Math.random() / 10},
      {name: '6', 2011:Math.random() / 10},
      {name: '8', 2011: Math.random() / 10},
      {name: '10', 2011:Math.random() / 10},
      {name: '12', 2011: Math.random() / 10},
      {name: '14', 2011:Math.random() / 10},
      {name: '16', 2011: Math.random() / 10},
      {name: '18', 2011: Math.random() / 10},
      {name: '20', 2011: Math.random() / 10},
      {name: '22', 2011: Math.random() / 10},
      {name: '24', 2011: Math.random() / 10},
    ]
    x(newData)
  },2000)
})


    const x = (data) =>{
      myChart.value.setOption(createEchartsOptions({
        xAxis: {
          type: 'category',
          boundaryGap: false,
          data:data.map(i=>i.name),
          splitLine: {show: true, lineStyle: {color: '#073E78'}},
          axisTick: {show: false},
          axisLine: {show: false},

        },
        grid: {
          x: px(20),
          x2: px(20),
          y: px(20),
          y2: px(20),
          containLabel: true
        },
        yAxis: {
          type: 'value',
          splitLine: {lineStyle: {color: '#073E78'}},
          axisLine: {
            show: true,
            lineStyle: {color: '#073E78'}
          },
          axisLabel: {
            formatter(val) {
              return val * 100 + '%';
            }
          }
        },
        series: [
          {
            data:data.map(i=>i[2011]),
            type: 'line',
            symbol: 'circle',
            symbolSize: px(12),
            lineStyle: {width: px(2)},
            areaStyle: {
              color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [{
                offset: 0,
                color: '#414a9f'
              }, {
                offset: 1,
                color: '#1b1d52'
              }]),
            },

          }
        ]


      }))
    }

    onMounted(() => {
      myChart.value = echarts.init(divRef.value)
     x(data)

    })
    return {divRef}
  },

}



</script>

<style lang="scss" scoped>
@import "../assets/css.scss";
.时段分析{
  height: 363/ 2420 * 100rem;
}

</style>
