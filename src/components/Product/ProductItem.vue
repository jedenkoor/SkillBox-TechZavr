<template>
  <li class="catalog__item">
    <router-link
      class="catalog__pic"
      :to="{ name: 'product', params: { id: product.id } }"
    >
      <img :src="product.image" :alt="product.title" />
    </router-link>
    <h3 class="catalog__title">
      <router-link :to="{ name: 'product', params: { id: product.id } }">{{
        product.title
      }}</router-link>
    </h3>
    <span class="catalog__price">{{ product.price | numberFormat }}</span>

    <ProductColors
      :colors="product.colors"
      :currentColor.sync="currentColor"
      class="colors--black"
    />
  </li>
</template>

<script>
import numberFormat from "@/functions/numberFormat";

import ProductColors from "@/components/Product/ProductColors";

export default {
  props: ["product"],
  data() {
    return {
      currentColor: this.product.colors[0].id,
    };
  },
  components: {
    ProductColors,
  },
  filters: {
    numberFormat,
  },
};
</script>

<style lang="scss">
.colors--black {
  --border-color: #222;
}
</style>