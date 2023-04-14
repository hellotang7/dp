<script setup>
import HelloWorld from './components/header.vue'
import Chart1 from './components/chart1.vue'


</script>

<template>
  <div class="home">
    <HelloWorld/>
    <main>
      <section class="section1">
        <Chart1/>
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

  }
}

</style>
