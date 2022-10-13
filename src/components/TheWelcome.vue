<script setup lang="ts">
import SimpleStockPrice from "@/components/SimpleStockPrice.vue";
</script>

<template>
  <div class="price-wrapper">
    <SimpleStockPrice ticker="AAPL" />
    <SimpleStockPrice ticker="TSLA" />
    <SimpleStockPrice ticker="AMZN" />
  </div>
</template>

<style lang="less" scoped>
.price-wrapper {
  display: flex;
  gap: 32px;
}
</style>
