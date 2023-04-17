<template>
  <div class="bordered 破获排名">
    <h2>案件破获排名</h2>
    <div ref="divRef" class="chart"></div>
    <div class="legend">
      <span class="first"/> 破案排名1
      <span class="second"/> 破案排名2
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
    const myChart = ref(null)
    const data = [
      {name: '城关区公安局', 2011: 2, 2012: 3},
      {name: '七里河区公安局', 2011: 2, 2012: 3},
      {name: '西固区公安局', 2011: 2, 2012: 3},
      {name: '安宁区公安局', 2011: 2, 2012: 3},
      {name: '红古区公安局', 2011: 2, 2012: 3},
      {name: '永登县公安局', 2011: 2, 2012: 3},
      {name: '皋兰县公安局', 2011: 2, 2012: 3},
      {name: '榆中县公安局', 2011: 2, 2012: 3},
      {name: '新区公安局', 2011: 2, 2012: 3},
    ]

    onMounted(() => {
      setInterval(() => {
        const newData = [
          {name: '城关区公安局', 2011: 2, 2012: Math.random() * 10},
          {name: '七里河区公安局', 2011: 2, 2012: 3},
          {name: '西固区公安局', 2011: 2, 2012: 3},
          {name: '安宁区公安局', 2011: 2, 2012: 3},
          {name: '红古区公安局', 2011: 2, 2012: 3},
          {name: '永登县公安局', 2011: 2, 2012: 3},
          {name: '皋兰县公安局', 2011: 2, 2012: 3},
          {name: '榆中县公安局', 2011: 2, 2012: 3},
          {name: '新区公安局', 2011: 2, 2012: 3},
        ]
        x(newData)
      },1000)
    })

    const x = (data) => {
      myChart.value.setOption(createEchartsOptions({

        xAxis: {
          type: 'value',
          boundaryGap: [0, 0.01],
          splitLine: {show: false},
          axisLabel: {show: false},
        },

        yAxis: {
          axisTick: {show: false},
          axisLabel: {
            margin: px(10),
            formatter(val) {
              return val.replace('公安局', '\n公安局');
            }
          },
          type: 'category',
          data: data.map(i => i.name)
        },

        series: [

          {
            name: '2011年',
            type: 'bar',
            data: data.map(i => i[2011]),
            itemStyle: {
              normal: {
                color: new echarts.graphic.LinearGradient(0, 0, 1, 0, [{
                  offset: 0,
                  color: '#2034f9'
                }, {
                  offset: 1,
                  color: '#04a1ff'
                }]),
              }
            }
          },
          {
            name: '2012年',
            type: 'bar',
            data: data.map(i => i[2012]),
            itemStyle: {
              normal: {
                color: new echarts.graphic.LinearGradient(0, 0, 1, 0, [{
                  offset: 0,
                  color: '#b92ae8'
                }, {
                  offset: 1,
                  color: '#6773e7'
                }]),
              }
            }
          }
        ],
      }))
    }
    onMounted(() => {
      myChart.value = echarts.init(divRef.value)
      x(data)
    })
    return {divRef}
  }
}
</script>

<style lang="scss" scoped>
@import "../assets/css.scss";

.破获排名 {
  height: 423/ 2420 * 100rem;

  .legend {
    display: flex;
    align-items: center;
    justify-content: flex-end;
    width: 100%;
    padding: 0 20 / 2420 * 100rem 10 / 2420 * 100rem;

    > .first, > .second {
      display: inline-block;
      width: 18 / 2420 * 100rem;
      height: 12 / 2420 * 100rem;
      margin: 0 10 / 2420 * 100rem;
    }

    .first {
      background: linear-gradient(90deg, #2034f9 0%, #04a1ff 100%);
    }

    .second {
      background: linear-gradient(90deg, #b92ae8 0%, #6773e7 100%);
    }
  }
}

</style>
