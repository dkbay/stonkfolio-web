<script setup lang="ts">
import axios from 'axios';
import { reactive } from 'vue';

const props = defineProps({
  ticker: String,
});

let url =
  "https://api.polygon.io/v2/aggs/ticker/" +
  props.ticker +
  "/prev?adjusted=true&apiKey=" +
  import.meta.env.VITE_POLYGON_API_KEY;

const state = reactive({
  data: {},
});

const fetchData = () => {
  axios.get(url).then((response) => {
    state.data = response.data.results[0];
  });
};

fetchData();
</script>

<template>
  <div class="simple-price">
    <div>
      <h1 class="simple-price__ticker">{{ props.ticker }}</h1>
    </div>
    <div class="simple-price__price-wrapper">
      <p class="simple-price__price"><span>open</span>{{ state.data.o }}</p>
      <p class="simple-price__price"><span>close</span>{{ state.data.c }}</p>
    </div>
  </div>
</template>

<style lang="less" scoped>
.simple-price {
  border-radius: 8px;
  background-color: #333;
  padding: 16px 24px;
  max-width: max-content;

  &__ticker {
    margin: 0;
    color: #f3f3f3;
    font-size: 1.25em;
  }

  &__price-wrapper {
    display: flex;
    gap: 16px;
  }

  &__price {
    display: flex;
    gap: 8px;
    color: #f3f3f3;
    margin: 0;
    font-size: 18px;
    font-weight: normal;

    & > span {
      font-size: 14px;
      align-self: center;
    }
  }
}
</style>
