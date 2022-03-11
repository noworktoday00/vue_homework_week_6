<template>
  <FrontNavBar></FrontNavBar>
  <div class="container my-5">
    <div class="row my-5">
      <router-view></router-view>
    </div>
  </div>
  <div class="container-fluid bg-dark fixed-bottom mt-3">
    <div class="row">
      <div class="col">
        <p class="text-center text-light">好想打球工作室</p>
      </div>
    </div>
  </div>
</template>

<script>
import FrontNavBar from "@/components/FrontNavBar.vue";
export default {
  components: {
    FrontNavBar,
  },
};
</script>
