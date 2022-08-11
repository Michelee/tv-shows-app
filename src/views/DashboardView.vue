<template>
  <div class="dashboardContainer">
    <FiltersBox :categories="categories" @change="handleFilters" />
    <div class="tvGrid">
      <MainShow :show="getMainShow" />
      <TvCard
        v-for="(show, index) in filteredShows"
        :show="show"
        :key="show.id"
        v-show="index !== 0"
      />
    </div>
  </div>
</template>

<script>
import axios from "axios";

import FiltersBox from "@/components/FiltersBox.vue";
import MainShow from "@/components/MainShow.vue";
import TvCard from "@/components/TvCard.vue";

export default {
  name: "DashboardView",
  components: {
    FiltersBox,
    MainShow,
    TvCard,
  },
  data() {
    return {
      tvShows: [],
      filteredShows: [],
      filters: [],
      categories: [],
    };
  },
  async mounted() {
    const { data } = await axios.get("https://api.tvmaze.com/schedule");
    let list = [];
    const genres = [];

    data.forEach(({ show }) => {
      const index = list.findIndex((el) => el.id === show.id);
      genres.push(...show.genres);
      if (index === -1) {
        list.push(show);
      }
    });

    list = this.orderList(list);

    this.categories = [...new Set(genres)];
    this.tvShows = [...list];
    this.filteredShows = [...list];
  },
  methods: {
    handleFilters(event) {
      const { name, checked } = event.target;
      if (checked) {
        this.filters.push(name);
      } else {
        const index = this.filters.indexOf(name);
        const currentFilters = this.filters;
        currentFilters.splice(index, 1);
        this.filters = currentFilters;
      }

      const allTvShows = this.tvShows;
      const programs = [];

      if (this.filters.length) {
        console.log(this.filters);
        this.filters.forEach((filter) => {
          programs.push(
            ...allTvShows.filter(
              (show) =>
                show.genres.includes(filter) &&
                programs.findIndex((i) => i.id === show.id) === -1
            )
          );
        });

        this.filteredShows = this.orderList(programs);
      } else {
        this.filteredShows = this.orderList(allTvShows);
      }
    },
    orderList(list) {
      return list.sort((a, b) => b.rating?.average - a.rating?.average);
    },
  },
  computed: {
    getMainShow() {
      return this.filteredShows.length ? this.filteredShows[0] : {};
    },
  },
};
</script>

<style scoped>
.dashboardContainer {
  display: flex;
  width: 100%;
}

.tvGrid {
  display: flex;
  flex-wrap: wrap;
  align-items: flex-start;
  width: 80%;
  margin: 0 auto;
}
</style>
