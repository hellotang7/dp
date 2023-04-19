<template>
  <div class="bordered 籍贯">
    <h2>犯罪人员籍贯分布地</h2>
<!--    <div>Counter: {{ Counter.value }}</div>-->
    <div className="wrapper">
      <div ref="divRef" class="chart"></div>
      <div class="ld">
        <div class="ring">
          <div class="radar"></div>
        </div>
        <p>数据实时监控中</p>
      </div>
      <p class="注释">该地图仅显示中国部分地区</p>
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

    // onMounted( setInterval(() => {
    //   Counter.value++  //变量名.value ++
    // }, 1000))



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

@keyframes spin {
  0% {
    -webkit-transform: rotate(0deg);
  }

  50% {
    -webkit-transform: rotate(180deg);
  }

  100% {
    -webkit-transform: rotate(360deg);
  }

}

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

    .注释 {
      color: #999;
      position: absolute;
      bottom: 40 / 2420 * 100rem;
      right: 55 / 2420 * 100rem;
    }

    .ld {
      position: relative;

      p {
        position: absolute;
        bottom: 40 / 2420 * 100rem;
        left: 75 / 2420 * 100rem;
        font-size: 10 / 2420 * 100rem;
        color: #999;
      }


      .ring {
        font-size: 15.093333333333332px;
        -webkit-font-smoothing: antialiased;
        font-family: -apple-system, "Noto Sans", "Helvetica Neue", Helvetica, "Nimbus Sans L", Arial, "Liberation Sans", "PingFang SC", "Hiragino Sans GB", "Noto Sans CJK SC", "Source Han Sans SC", "Source Han Sans CN", "Microsoft YaHei", "Wenquanyi Micro Hei", "WenQuanYi Zen Hei", "ST Heiti", SimHei, "WenQuanYi Zen Hei Sharp", sans-serif;
        color: #fff;
        box-sizing: border-box;
        margin: 0;
        padding: 0;
        font-weight: 400;
        border: 1px solid #0c2939;
        position: absolute;
        bottom: 75 / 2420 * 100rem;
        left: 75 / 2420 * 100rem;
        width: 120 / 2420 * 100rem;
        height: 120 / 2420 * 100rem;
        border-bottom: none;
        border-radius: 50%;
        overflow: hidden;
        animation: spin infinite 5s linear;

        .radar {
          font-size: 15.093333333333332px;
          -webkit-font-smoothing: antialiased;
          font-family: -apple-system, "Noto Sans", "Helvetica Neue", Helvetica, "Nimbus Sans L", Arial, "Liberation Sans", "PingFang SC", "Hiragino Sans GB", "Noto Sans CJK SC", "Source Han Sans SC", "Source Han Sans CN", "Microsoft YaHei", "Wenquanyi Micro Hei", "WenQuanYi Zen Hei", "ST Heiti", SimHei, "WenQuanYi Zen Hei Sharp", sans-serif;
          color: #fff;
          box-sizing: border-box;
          margin: 0;
          padding: 0;
          font-weight: 400;
          border: 2px solid #103142;
          position: absolute;
          width: 3.375rem;
          height: 3.375rem;
          top: 50%;
          left: 50%;
          transform: translate(-50%, -50%);
          border-radius: 50%;
        }

        .radar::before {
          content: "";
          position: absolute;
          top: 50%;
          left: 50%;
          transform: translate(-50%, -50%);
          width: 1.75rem;
          height: 1.75rem;
          border: 2px solid #082132;
          border-radius: 50%;
        }

        .radar::after {
          content: "";
          position: absolute;
          top: 0;
          left: 50%;
          transform: translateX(-50%);
          width: .125rem;
          height: 1.5rem;
          z-index: 1;
          background: #007cc0;
          border-radius: 50%;
          box-shadow: 0 0 5px 1px #0094e4, -3px -10px 5px 1px #0094e4, -7px -15px 10px 1px #0094e4, -3px -3px 10px 1px #0094e4, -7px -7px 20px 1px #0094e4, -11px -11px 30px 1px #0094e4, -11px -11px 40px 1px #0094e4, -11px -11px 30px 1px #0094e4, -11px -11px 30px 1px #0094e4;
        }
      }
    }
  }
}
</style>
