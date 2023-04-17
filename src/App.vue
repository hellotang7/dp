<script setup>
import Chart1 from './components/chart1.vue'
import Chart2 from "./components/chart2.vue";
import Chart3 from "./components/chart3.vue";
import Chart4 from "./components/chart4.vue";
import Chart5 from "./components/chart5.vue";
import Chart6 from "./components/chart6.vue";
import Chart7 from "./components/chart7.vue";
import Chart8 from "./components/chart8.vue";
import Chart9 from "./components/chart9.vue";
import Chart10 from "./components/chart10.vue";
import Chart11 from "./components/chart11.vue";
import Chart12 from "./components/chart12.vue";
import Chart13 from "./components/chart13.vue";
import Chart14 from "./components/chart14.vue";
</script>

<template>
  <div class="home">
    <header></header>
    <main>

      <section class=" section1">
        <Chart1/>
        <Chart2/>
      </section>

      <section class=" section2">
        <Chart3/>
        <Chart4/>
      </section>

      <section class="bordered section3">
        <Chart5/>
      </section>

      <section class="section4">
        <Chart6/>
        <div class="bordered 年龄段">
          <h2>犯罪人员年龄分布</h2>
          <div class="charts">
            <Chart7/>
            <Chart8/>
            <Chart9/>
          </div>
        </div>
      </section>

      <section class="section5">
        <div class="bordered row1 案发类型">
          <h2>案发类型统计</h2>
          <div class="charts">
            <Chart10/>
            <Chart11/>
          </div>
        </div>
        <div class="bordered row2 案发街道">
          <h2>案发街道统计</h2>
          <div class="charts">
            <Chart12/>
            <Chart13/>
          </div>
        </div>
        <div class="bordered row3 作案手段">
          <h2>作案手段分析</h2>
          <Chart14/>
        </div>
      </section>
    </main>
    <footer>
      &copy; 幺六零八 2022-2023
    </footer>
  </div>
</template>

<style lang="scss" scoped>

.home {
  flex: 1;
  display: flex;
  flex-direction: column;
  background: #010310;
  color: white;
  font-size: 16 / 2420 * 100rem;

  header {
    width: 2420 / 2420 * 100rem;
    margin: 0 auto;
    height: 99/ 2420 * 100rem;
    background-size: cover;
    background-image: url("./assets/header.png");
  }

  footer {
    margin: 20 / 2420 * 100rem 0 1 / 2420 * 100rem;
    height: 68 / 2420 * 100rem;
    border-top: 2px solid #0d2d59;
    border-bottom: 2px solid #0d2d59;
    background: #0c0d2b;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  main {
    width: 2420/ 2420 * 100rem;
    margin: 0 auto;
    padding-top: 30 / 2420 * 100rem;
    flex: 1;
    display: grid;
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
      background: #0f113a;
      color: white;

      &::before {
        pointer-events: none;
        content: '';
        position: absolute;
        left: 0;
        right: 0;
        bottom: 0;
        top: 0;
        border-radius: 4px;
        box-shadow: 17px 0 0 -16px #0e325f,
        -17px 0 0 -16px #0e325f,
        0 17px 0 -16px #0e325f,
        0 -17px 0 -16px #0e325f,
        9px 0 0 -8px #0d4483,
        -9px 0 0 -8px #0d4483,
        0 9px 0 -8px #0d4483,
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

      .年龄段 {
        height: 363 / 2420 * 100rem;

        .charts {
          padding: 30 / 2420 * 100rem;
        }
      }
    }
    > .section5 {
      grid-area: box5;

      > .row1 {
        height: 317 / 2420 * 100rem;
      }

      > .row2 {
        height: 317 / 2420 * 100rem;
      }

      > .row3 {
        height: 455 / 2420 * 100rem;
      }
    }





    .年龄段,.案发类型, .案发街道, .作案手段{
      display: flex;
      flex-direction: column;

      h2 {
        display: inline-block;
        flex-shrink: 0;
        border: 1px solid #0a5299;
        border-bottom-left-radius: 4px;
        border-bottom-right-radius: 4px;
        font-size: 22 / 2420 * 100rem;
        line-height: 24 / 2420 * 100rem;
        padding: 10 / 2420 * 100rem 28 / 2420 * 100rem;
        text-shadow: 0 0 3 / 2420 * 100rem white;
      }
      .charts{
      width: 100%;
      flex: 1;
      display: flex;
      }
    }
    .section1,.section2,.section4,.section5{
      display: flex;
      flex-direction: column;
      justify-content: space-between;
    }



  }
}

</style>
