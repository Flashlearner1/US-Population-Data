<template>
  <div class="data">
    <h1>US POPULATION DATA</h1>
    <button class="button" @click="fetchData">Fetch Data</button>
    <br><br>
    <table class="table" style="width:50%">
  <tr>
    <th>Nation</th>
    <th>Population</th>
    <th>Year</th>
  </tr>

  <tr class="row" v-for="item in data" :key="item.ID">
    <td>{{ item.Nation }}</td>
    <td>{{ item.Population }}</td>
    <td>{{ item.Year }}</td>
  </tr>
  <tr class="row" v-for="item in data" :key="item.ID">
    <td>{{ item.Nation }}</td>
    <td>{{ item.Population }}</td>
    <td>{{ item.Year }}</td>
  </tr>

</table>
  </div>
</template>

<script>
export default {
  data() {
    return {
      data: []
    };
  },
  mounted() {
    this.fetchData();
  },
  methods: {
    async fetchData() {
      try {
        const response = await fetch('https://datausa.io/api/data?drilldowns=Nation&measures=Population');
        const jsonData = await response.json();
        this.data = jsonData.data;
      } catch (error) {
        console.error('Error fetching data:', error);
      }
    }
  }
};
</script>

