<template>
  <div class="作案手段">
    <table>
      <thead>
      <tr>
        <th colspan="2">类型</th>
        <th>单数</th>
        <th>总计</th>
      </tr>
      </thead>
      <tbody>
      <tr>
        <td rowspan="4">入室盗窃</td>
        <td>翻窗入室</td>
        <td>10</td>
        <td rowspan="4">80</td>
      </tr>
      <tr>
        <td>撬门入室</td>
        <td>20</td>
      </tr>
      <tr>
        <td>技术开锁</td>
        <td>20</td>
      </tr>
      <tr>
        <td>撬防护栏</td>
        <td>30</td>
      </tr>
      <tr>
        <td rowspan="2">抢夺</td>
        <td>摩托车飞车抢夺</td>
        <td>22</td>
        <td rowspan="2">44</td>
      </tr>
      <tr>
        <td>徒手抢夺</td>
        <td>22</td>
      </tr>
      <tr>
        <td rowspan="3">扒窃</td>
        <td>公交车扒窃</td>
        <td>40</td>
        <td rowspan="3">68</td>
      </tr>
      <tr>
        <td>车站扒窃</td>
        <td>22</td>
      </tr>
      <tr>
        <td>街面扒窃</td>
        <td>45</td>
      </tr>
      <tr>
        <td rowspan="2">诈骗</td>
        <td>甩票子诈骗</td>
        <td>32</td>
        <td rowspan="2">102</td>
      </tr>
      <tr>
        <td>买手机诈骗</td>
        <td>80</td>
      </tr>
      </tbody>
    </table>
  </div>
</template>

<script>


</script>

<style lang="scss" scoped>
//@import "../assets/css.scss";

.作案手段 {
  height: 100%;


  > table {
    width: 95%;
    table-layout: fixed;
    //margin-top: px(25);
    margin:  18 / 2420 * 100rem ;
    border-collapse: collapse;

    th, td {
      border: 1px solid #1a3671;
    }

    thead {
      th {
                height: 60 / 2420 * 100rem;
                box-shadow: inset 0 0 60 / 2420 * 100rem 0 #1f3d85;
      }
    }

    tbody {
      td {
              height: 28 / 2420 * 100rem;
                width: 84 / 2420 * 100rem;
                background: #1c2456;
      }
    }
  }
}


</style>
