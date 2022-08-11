<template>
  <article class="tvCard">
    <img :src="show?.image.original" alt="show-image" />
    <div class="showDetails">
      <h1>{{ show.name }}</h1>
      <span
        >{{ timeConvert }} <span class="divider">|</span> {{ show.type }}</span
      >
      <div class="rating" v-show="show.rating.average">
        <StarIcon /> <span>{{ show.rating.average }} / 10</span>
      </div>
    </div>
  </article>
</template>

<script>
import StarIcon from "@/components/icons/StarIcon.vue";

export default {
  name: "TvCard",
  components: {
    StarIcon,
  },
  props: {
    show: Object,
  },
  computed: {
    timeConvert() {
      const time = this.show.runtime;
      var hours = Math.floor(time / 60);
      var minutes = time % 60;

      return `${hours ? `${hours}h` : ""} ${minutes ? `${minutes}min` : ""}`;
    },
  },
};
</script>

<style scoped>
.tvCard {
  display: flex;
  flex-direction: column;
  padding: 0 10px;
  margin-bottom: 30px;
  width: 250px;
}

img {
  width: 250px;
  height: 350px;
}

.showDetails {
  text-align: left;
}

h1 {
  font-size: 16px;
  text-transform: uppercase;
  color: white;
  margin-bottom: 10px;
}

span {
  color: grey;
  font-size: 12px;
}

.divider {
  display: inline-block;
  margin: 0 10px;
}

.rating {
  margin-top: 8px;
  display: flex;
  align-items: center;
}

svg {
  margin-right: 10px;
}
</style>
