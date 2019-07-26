<template>
  <div>
    <ProductInfo :product="product" />
    <!-- http://localhost:8080/product/1 -->
    <!-- 路线.参考.id: property id of object params. coming from routerlink in ProductCard.vue -->
    <!-- {{ $route.params.id }} -->
    <!-- {{ id }} -->
  </div>
</template> 
<script>
import { mapGetters } from "vuex";
import ProductInfo from "@/components/ProductInfo.vue";

// any dynamic id will be sent as a props
export default {
  components: { ProductInfo },

  data() {
    return {
      product: ""
    };
  },

  props: {
    id: {
      type: Number,
      required: true
    }
  },

  computed: mapGetters(["getProductById"]),

  // if don't have computed, use $store.getters.getProductById(this.id)
  created() {
    this.product = this.getProductById(this.id);
    console.log(this.product);
  }
};
</script>