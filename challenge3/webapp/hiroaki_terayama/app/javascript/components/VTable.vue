<template>
  <div>
    <table class="table">
      <thead>
        <tr>
          <th>area</th>
          <th v-for="month in labels" :key="month">{{ month }}</th>
          <th>Average</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>energy production(all area)</td>
          <td v-for="data in allData">{{ round(data) }}</td>
          <td>{{ aveAll }}</td>
        </tr>
        <tr>
          <td>energy production(your area)</td>
          <td v-for="data in selectedData">{{ round(data) }}</td>
          <td>{{ aveSelected }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
  import Labels from '../shared/labels'

  export default {
    props: ['allData', 'selectedData', 'aveAll', 'aveSelected'],
    data () {
      return {
        labels: Labels.monthLabels,
      }
    },
    methods: {
      round (value) {
        return Math.round(value * 10) / 10
      }
    },
  }
</script>