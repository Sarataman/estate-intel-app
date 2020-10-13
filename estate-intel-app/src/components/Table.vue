<template>
  <div class="table-border">
    <table class="main-table">
      <thead>
        <tr>
            <th class="first-col">Project Name</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for='result in results' :key='result.id'>
          <td class="first-col fixed-col">{{ result.project_name }}</td>
        </tr>
      </tbody>
    </table>
    <div class="sec-table">
      <table>
        <thead>
          <tr>
            <!-- hidden-col class scrollable Project name in mobile version -->
            <!-- <th class="hidden-col">Project Name</th> -->
            <th>Developer</th>
            <th>Main Contractor</th>
            <th>Area</th>
            <th>State</th>
            <th>Status</th>
            <th class="last-col">Sector</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for='result in results' :key='result.id'>
            <!-- <td class="hidden-col">{{result.project_name}}</td> -->
            <td>{{ result.developer }}</td>
            <td>{{ result.main_contractor }}</td>
            <td>{{ result.lga }}</td>
            <td>{{ result.state }}</td>
            <td class="status">
              <div class="status-bg">{{ result.status }}</div>
            </td>
            <td>{{ result.sector }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'Table',
  data () {
    return {
      results: []
    }
  },
  mounted () {
    axios
      .get('https://70c5b72c-65db-4a66-ba01-3e14763157e8.mock.pstmn.io/')
      .then(response => { this.results = response.data.data })
      .catch(function (error) {
        console.log(error)
      })
  }
}
</script>

<style scoped>
.table-border {
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 0 1%;
}

table {
  border-collapse: collapse;
}

.main-table {
  box-shadow: -5px 5px 10px #3738381a, 5px 5px 10px #3738381a;
}

th,td {
  padding: 25px 15px;
  white-space: nowrap;
  text-align: left;
}

.first-col {
  border-radius: 5px 0 0 0 ;
  font-weight: bold;
}

.last-col {
  border-radius: 0 5px 0 0;
  box-shadow: 5px 5px 10px #3738381a;
}

tr:nth-child(even) {
  background: #ffffff;
}

th {
  background: #27394b;
  color: #ffffff;
  font-weight: 600;
}

.main-table {
  float: left;
}

.sec-table {
  overflow: auto;
  box-shadow: -2px 3px 10px #3738381a;
}

/* .hidden-col {
  display: none;
} */

@media (max-width: 92em) {
  .table-border {
    display: block;
  }
}

@media (max-width: 50em) {

  /* .hidden-col {
    display: block;
    font-weight: bold;
    box-shadow: 5px 5px 8px #7375791a;
    border-radius: 5px 0 0 0;
  } */

  .table-border {
    font-size: 12px;
  }

  .sec-table {
    border-radius: 0 5px 0 0;
  }
}

.status{
  padding: 20px 10px;
}

.status-bg {
  background: rgb(255, 222, 179);
  color: #967a46;
  padding: 5px;
  border-radius: 2px;
}

</style>
