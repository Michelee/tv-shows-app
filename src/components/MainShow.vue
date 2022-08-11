<template>
  <article class="mainShowComp">
    <div class="showDetails">
      <div class="bestScored" v-show="show?.rating?.average">Best Scored</div>
      <br />
      <span>{{ show?.type }}</span>
      <h1>{{ show?.name }}</h1>
      <span v-show="show?.rating?.average"
        ><span class="rating">{{ show?.rating?.average }}</span> / 10</span
      >
      <p class="summary" v-html="show?.summary"></p>
    </div>
    <img :src="show?.image?.original" alt="main show" />
  </article>
</template>

<script>
export default {
  name: "MainShow",
  props: {
    show: Object,
  },
};
</script>

<style scoped>
.mainShowComp {
  display: flex;
  width: 100%;
  color: white;
  margin-bottom: 50px;
}

.bestScored {
  background: #42b983;
  color: white;
  padding: 3px 5px;
  border-radius: 5px;
  display: inline-block;
  font-weight: bold;
  margin-bottom: 30px;
}

img {
  width: 300px;
  height: auto;
}

.showDetails {
  text-align: left;
  margin-right: 30px;
}

span {
  color: #808080;
}

h1 {
  font-size: 58px;
  margin: 10px 0;
}

.rating {
  color: #42b983;
  font-size: 50px;
  font-weight: bold;
}

.summary {
  max-width: 600px;
}
</style>
