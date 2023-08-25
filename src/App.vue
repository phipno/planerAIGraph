<script>
import Filters from './components/Filters.vue';
import BarChart from './components/BarChart.vue';

export default {
  components: {
    Filters,
    BarChart,
  },
  data() {
    return {
      allData: [],
      filteredData: [],
    };
  },
  methods: {
    handleFilterChange(filteredData) {
      this.filteredData = filteredData;
    },
  },
  created() {
    // For the purpose of this example, generating dummy data
    this.allData = [
      { product: 'Bread', store: 'Store A', recommendation: 100, delivery: 110 },
      { product: 'Cake', store: 'Store B', recommendation: 50, delivery: 60 },
      // Add more data entries
    ];
    this.filteredData = this.allData; // Initially display all data
  },
};
</script>

<template>
  <div class="app-container">
    <Filters @filter-change="handleFilterChange" />
    <Graph :data="filteredData" />
  </div>
</template>

<style>
  .app-container {
    width: 800px;
    position: flex;
    margin-left: calc((100% - 60%) / 2);
    justify-content: center; /* Center horizontally */
    height: 450px;
  }
</style>
