<template>
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark fixed-top">
    <div class="container-fluid">
      <a class="navbar-brand" href="#">羽你交流</a>
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarSupportedContent"
        aria-controls="navbarSupportedContent"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav me-auto mb-2 mb-lg-0">
          <li class="nav-item">
            <router-link class="nav-link active" to="/admin/adminproducts">
              後台產品列表
            </router-link>
          </li>
          <li class="nav-item">
            <router-link class="nav-link active" to="/admin/coupon">
              後台優惠券
            </router-link>
          </li>
          <li class="nav-item">
            <router-link class="nav-link active" to="/"> 前往前台 </router-link>
          </li>
        </ul>
        <form class="d-flex">
          <input
            class="form-control me-2"
            type="search"
            placeholder="Search"
            aria-label="Search"
          />
          <button class="btn btn-outline-success" type="submit">Search</button>
        </form>
      </div>
    </div>
  </nav>
  <div class="container my-5">
    <div class="row my-5">
      <router-view></router-view>
    </div>
  </div>
  <div class="container-fluid bg-dark fixed-bottom">
    <div class="row">
      <div class="col">
        <p class="text-center">好想打球工作室</p>
      </div>
    </div>
  </div>
</template>
