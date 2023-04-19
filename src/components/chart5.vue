<template>
  <div class=" 战果对比">
    <h2>往年战果数对比</h2>
    <table>
      <thead>
      <tr>
        <th>年份</th><th>破案数</th><th>抓获嫌疑人</th><th>并串案件</th><th>现勘录入</th>
        <th>视侦录入</th><th>合成案件数</th><th>合计</th>
      </tr>
      </thead>
      <tbody>
      <tr>
        <td>2015</td><td>2</td><td>3</td><td>4</td><td>5</td><td>6</td><td>7</td><td>8</td>
      </tr>
      <tr>
        <td>2016</td><td>2</td><td>3</td><td>4</td><td>5</td><td>6</td><td>7</td><td>8</td>
      </tr>
      <tr>
        <td>2017</td><td>2</td><td>3</td><td>4</td><td>5</td><td>6</td><td>7</td><td>8</td>
      </tr>

      </tbody>
    </table>
  </div>
</template>

<script>


</script>

<style lang="scss" scoped>
@import "../assets/css.scss";

.战果对比 {
  height: 100%;

  > table {
    margin-top: 38 / 2420 * 100rem;
    border-collapse: collapse;
    th, td {
      border: 1px solid #1a3671;
    }
    thead {
      th {
        height: 70 / 2420 * 100rem;
        box-shadow: inset 0 0 60 / 2420 * 100rem 0 #1f3d85;
      }
    }
    tbody {
      td {
        height: 50 / 2420 * 100rem;
          width: 88 / 2420 * 100rem;
          background: #1c2456;
      }

    }
  }
}

</style>
