<template>
  <table class="table align-middle">
    <thead>
      <tr>
        <th>圖片</th>
        <th>商品名稱</th>
        <th>價格</th>
        <th></th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="item in products" :key="item.id">
        <td style="width: 200px">
          <div
            :style="{ backgroundImage: `url(${item.imageUrl})` }"
            style="
              height: 100px;
              background-size: cover;
              background-position: center;
            "
          ></div>
        </td>
        <td>{{ item.title }}</td>
        <td>
          <div class="h5" v-if="item.origin_price === item.price">
            {{ item.price }} 元
          </div>
          <div v-else>
            <del class="h6">原價 {{ item.origin_price }} 元</del>
            <div class="h5">現在只要 {{ item.price }} 元</div>
          </div>
        </td>
        <td>
          <div class="btn-group btn-group-sm">
            <button
              type="button"
              class="btn btn-outline-secondary"
              @click="openProductModal(item.id)"
            >
              <i
                class="fas fa-spinner fa-pulse"
                v-show="isLoadingItem === item.id"
              ></i>
              查看更多
            </button>
            <button
              type="button"
              class="btn btn-danger"
              @click="addToCart(item.id)"
            >
              <i
                class="fas fa-spinner fa-pulse"
                v-show="isLoadingItem === item.id"
              ></i>
              加到購物車
            </button>
          </div>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script>
export default {
  data() {
    return {
      products: [],
      tempProduct: [],
      productId: "",
      cartData: [],
      isLoadingItem: "",
      //建立表單內容 參照API格式
      form: {
        user: {
          name: "",
          email: "",
          tel: "",
          address: "",
        },
        message: "",
      },
    };
  },
  methods: {
    getProducts() {
      const url = `https://vue3-course-api.hexschool.io/v2/api/vanmoritz/products/all`;
      this.$http(url)
        .then((res) => {
          console.log(res);
          this.products = res.data.products;
        })
        .catch((err) => {
          alert(err.data.message);
        });
    },
    getCart() {
      //  購物車列表 https://vue3-course-api.hexschool.io/v2/api/vanmoritz/cart
      const url = `https://vue3-course-api.hexschool.io/v2/api/vanmoritz/cart`;
      this.$http(url)
        .then((res) => {
          console.log(res.data.data);
          this.cartData = res.data.data;
        })
        .catch((err) => {
          alert(err.data.message);
        });
    },
    addToCart(id, qty = 1) {
      //  加入購物車 https://vue3-course-api.hexschool.io/v2/api/vanmoritz/cart
      const url = `https://vue3-course-api.hexschool.io/v2/api/vanmoritz/cart`;
      const data = {
        product_id: id,
        qty,
      };
      this.isLoadingItem = id;
      this.$http(url, { data }).then((res) => {
        console.log(res);
        alert(res.data.message);
        this.getCart();
        this.isLoadingItem = "";
      });
    },
  },
  mounted() {
    this.getProducts();
    this.getCart();
  },
};
</script>
