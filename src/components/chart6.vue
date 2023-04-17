<template>
  <div class="bordered 籍贯">
    <h2>全市犯罪人员籍贯分布地</h2>
    <div className="wrapper">
      <div ref="divRef" class="chart"></div>
      <div class="legend bordered">
        <span class="icon" style="background-color: #15B8FD"/>甘肃籍
        <span class="icon" style="background-color: #06E1EE"/>四川籍
        <span class="icon" style="background-color: #BB31F7"/>青海籍
      </div>
    </div>
  </div>
</template>

<script>
import {onMounted, ref} from "vue";
import * as echarts from "echarts";
import china from "../assets/china.json"
import {px} from "../assets/px.js";

export default {
  setup() {
    const divRef = ref(null);
    const colors = {'青海省': '#BB31F7', '甘肃省': '#15B8FD', '四川省': '#06E1EE'};
    onMounted(() => {
      const myChart = echarts.init(divRef.value)
      echarts.registerMap('CN', china);

      myChart.setOption({
        xAxis: {show: false},
        yAxis: {show: false},
        series: [
          {
            type: 'map',
            mapType: 'CN', // 自定义扩展图表类型
            data: [
              {name: '甘肃省', value: 1},
            ],
            label: {show: false, color: 'white'},
            itemStyle: {
              areaColor: '#010D3D',
              color: colors['甘肃省'],
              borderColor: '#01A7F7',
              emphasis: {
                label: {color: 'white'},
                areaColor: '#5470C6',
              },
            }
          },
          {
            type: 'map',
            mapType: 'CN', // 自定义扩展图表类型
            data: [
              {name: '四川省', value: 100},
            ],
            itemStyle: {
              areaColor: '#010D3D',
              color: colors['四川省'],
              borderColor: 'yellow',
              emphasis: {
                label: {color: 'white'},
                areaColor: '#5470C6',
              },
            }
          },
          {
            type: 'map',
            mapType: 'CN', // 自定义扩展图表类型
            data: [
              {name: '青海省', value: 100},
            ],
            itemStyle: {
              areaColor: '#010D3D',
              color: colors['青海省'],
              borderColor: '#01A7F7',
              emphasis: {
                label: {color: 'white'},
                areaColor: '#5470C6',
              },
            }
          },

        ]


      })

    })
    return {divRef}
  },

}


</script>

<style lang="scss" scoped>
@import "../assets/css.scss";

.籍贯 {
  height: 753 / 2420 * 100rem;
  background: transparent;

  .wrapper {
    position: relative;
    width: 100%;
    flex: 1;
    display: flex;
    flex-direction: column;

    .chart {
      flex: 1;
    }

    .legend {
      position: absolute;
      top: 40 / 2420 * 100rem;
      left: 20 / 2420 * 100rem;
      display: flex;
      align-items: center;
      font-size: 22 / 2420 * 100rem;
      padding: 20 / 2420 * 100rem 10 / 2420 * 100rem 20 / 2420 * 100rem 0;
      border-radius: 0;


      .icon {
        margin: 0 10 / 2420 * 100rem;
        display: inline-block;
        width: 16 / 2420 * 100rem;
        height: 16 / 2420 * 100rem;
        border-radius: 50%;
        //background: #1cecd9;
      }
    }

  }
}
</style>
