<template>
  <div class="card text-center m-3">
    <table>
      <tr>
        <th>Регион</th>
        <th>Заражения</th>
        <th>Выздоровления</th>
        <th>Смерти</th>
      </tr>
      <tr v-for="item in totalVuePackages.russia_stat_struct.data" :key="item.info.name">
        <td>{{item.info.short_name}}</td>
        <td>{{item.info.cases}}   <sup><small>+{{item.info.cases_delta}}</small></sup></td>
        <td>{{item.info.cured}}   <sup><small>+{{item.info.cured_delta}}</small></sup></td>
        <td>{{item.info.deaths}}  <sup><small>+{{item.info.deaths_delta}}</small></sup></td>
      </tr>
    </table>
  </div>
</template>

<script>
  import axios from 'axios';

  export default {
    name: "get-request",
    data() {
      return {
        totalVuePackages: null
      };
    },
    created() {
      // Simple GET request using axios
      axios.get("https://yastat.net/s3/milab/2020/covid19-stat/data/v3/default_data.json")
              .then(response => this.totalVuePackages = response.data);
    }
  };
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
