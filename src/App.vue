<script setup>
import HelloWorld from './components/header.vue'
import * as echarts from 'echarts';
import { onMounted, ref } from 'vue'

const px = (n) => n /2420*pageWidth;
const divRef = ref(null);
onMounted(() => {
  // console.log(divRef.current)
  // console.log(divRef.value)
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

</script>

<template>
  <div class="home">
    <HelloWorld/>
    <main>
      <section class="section1">
        <div class="bordered 管辖统计">
          <h2>案发派出所管辖统计</h2>
          <div ref="divRef" class="chart"></div>
        </div>
      </section>
      <section class="bordered section2"></section>
      <section class="bordered section3"></section>
      <section class="bordered section4"></section>
      <section class="bordered section5"></section>
    </main>
  </div>
</template>

<style lang="scss" scoped>

.home {
  flex: 1;
  height: 100%;
  display: flex;
  flex-direction: column;
  background: #010310;
  color: white;

  > main {
    padding-top: 30 / 2420 * 100rem;
    flex: 1;
    display: grid;
    /*grid-template:
    "box1 box2 box4 box5" 755fr
    "box3 box3 box4 box5" 363fr / 366fr 361fr 811fr 747fr;*/
    grid-template-rows: 755fr 363fr;
    grid-template-columns: 366fr 361fr 811fr 747fr;
    grid-gap: 28 / 2420 * 100rem;
    grid-template-areas: 'box1 box2 box4 box5'
                       'box3 box3 box4 box5';

    .bordered {
      text-align: center;
      border: 1px solid #0764bc;
      border-radius: 4px;
      position: relative;
      box-shadow: 0 0 2px 0 #0e325f, inset 0 0 2px 0 #0e325f;
      background: #0c1139;
      color: white;

      &::before {
        content: '';
        position: absolute;
        left: 0;
        right: 0;
        bottom: 0;
        top: 0;
        border-radius: 4px;
        box-shadow: 17px 0 0 -16px #0e325f
                    -17px 0 0 -16px #0e325f
                    0 17px 0 -16px #0e325f
                    0 -17px 0 -16px #0e325f
                    9px 0 0 -8px #0d4483
                   -9px 0 0 -8px #0d4483
                    0 9px 0 -8px #0d4483
                    0 -9px 0 -8px #0d4483
      }
    }

    > .section1 {
      grid-area: box1;
    }

    > .section2 {
      grid-area: box2;
    }

    > .section3 {
      grid-area: box3;
    }

    > .section4 {
      grid-area: box4;

    }

    > .section5 {
      grid-area: box5;
    }
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
  }
}

</style>
