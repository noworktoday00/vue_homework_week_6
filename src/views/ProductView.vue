<template>
  <h2 class="mt-3">產品列表</h2>
  <div class="container my-5">
    <div class="row">
      <div class="col">
        <img class="img-fluid" :src="product.imageUrl" alt="" />
      </div>
      <div class="col">
        <h1>{{ product.title }}</h1>
        <p>{{ product.description }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      product: {},
    };
  },
  methods: {
    getProduct() {
      const { id } = this.$route.params;
      this.$http(
        // `${process.env.VUE_APP_API}/api/${process.env.VUE_APP_PATH}/products/all`
        `https://vue3-course-api.hexschool.io/v2/api/vanmoritz/product/${id}`
      ).then((res) => {
        this.product = res.data.product;
      });
    },
  },
  mounted() {
    this.getProduct();
  },
};
</script>
