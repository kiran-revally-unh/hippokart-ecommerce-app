<template>
  <li class="search-item dropdown-item p-2" v-if="product">
    <router-link
      class="product-link d-flex align-items-center text-left"
      :to="{
        name: 'ProductDetail',
        params: { id: product.id },
        query: { feature, exp: experimentCorrelationId },
      }"
      ><img :src="productImageUrl" class="product-img mr-2" alt="" />
      <span class="text-truncate">{{ product.name }}</span>
    </router-link>
  </li>
</template>

<script>

import { getProductImageUrl } from '../../../../util/getProductImageUrl';

export default {
  name: 'SearchItem',
  props: {
    product: { type: Object, required: true },
    feature: { type: String, required: true },
    experiment: { type: Object, required: false },
  },
  computed: {
    experimentCorrelationId() {
      return this.experiment?.correlationId;
    },
    productImageUrl() {
      return getProductImageUrl(this.product);
    },
  },
};
</script>

<style scoped>
.product-img {
  width: 40px;
}

.product-link {
  color: inherit;
}

.product-link:hover {
  text-decoration: none;
}
</style>
