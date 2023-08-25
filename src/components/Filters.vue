<template>
  <div>
    <select v-model="selectedStore">
      <option value="">All Stores</option>
      <option value="Store A">Store A</option>
      <option value="Store B">Store B</option>
      <!-- Add more store options -->
    </select>

    <select v-model="selectedProduct">
      <option value="">All Products</option>
      <option value="Bread">Bread</option>
      <option value="Cake">Cake</option>
      <!-- Add more product options -->
    </select>

    <button @click="applyFilters">Apply Filters</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      selectedStore: '',
      selectedProduct: '',
    };
  },
  methods: {
    applyFilters() {
      // Apply filters based on selectedStore and selectedProduct
      // Emit filter-change event with filtered data to App component
      const filteredData = this.$parent.allData.filter(item => {
        const storeMatch = !this.selectedStore || item.store === this.selectedStore;
        const productMatch = !this.selectedProduct || item.product === this.selectedProduct;
        return storeMatch && productMatch;
      });
      this.$emit('filter-change', filteredData);
    },
  },
};
</script>