<template>
  <div class="filtersContainer">
    <label>Search TV Show</label>
    <input placeholder="Show's name" />

    <div class="filterList">
      <h2>Filter By</h2>

      <CheckboxComp
        v-for="category in categories"
        :name="category"
        :value="category"
        :label="category"
        :key="category"
      />
    </div>
  </div>
</template>

<script>
import CheckboxComp from "@/components/Checkbox.vue";

export default {
  name: "FiltersBox",
  components: {
    CheckboxComp,
  },
  props: {
    categories: Array,
  },
};
</script>

<style scoped>
.filtersContainer {
  width: 20%;
  color: #808080;
  padding: 20px;
}

.filterList {
  text-align: left;
}
</style>
