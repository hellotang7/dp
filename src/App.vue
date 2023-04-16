<script setup>
import Chart1 from './components/chart1.vue'
import Chart2 from "./components/chart2.vue";
import Chart3 from "./components/chart3.vue";
import Chart4 from "./components/chart4.vue";
import Chart5 from "./components/chart5.vue";
import Chart6 from "./components/chart6.vue";
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
      </section>
      <section class="bordered section5">3</section>
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
        content: '';
        position: absolute;
        left: 0;
        right: 0;
        bottom: 0;
        top: 0;
        border-radius: 4px;
        box-shadow: 17px 0 0 -16px #0e325f
                    -17px 0 0 -16px #0e325f 0 17px 0 -16px #0e325f 0 -17px 0 -16px #0e325f 9px 0 0 -8px #0d4483
                   -9px 0 0 -8px #0d4483 0 9px 0 -8px #0d4483 0 -9px 0 -8px #0d4483
      }
    }

    > .section1 {
      grid-area: box1;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
    }

    > .section2 {
      grid-area: box2;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
    }

    > .section3 {
      grid-area: box3;
    }

    > .section4 {
      grid-area: box4;
      //display: flex;
      //flex-direction: column;
      //justify-content: space-between;
    }

    > .section5 {
      grid-area: box5;
    }

  }

}

</style>
