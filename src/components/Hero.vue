<template>
  <div class="hero">
    
    <!-- WEB -->
    <div class="d-none d-md-block">

      <div class="row mt-4">
        <div class="col-md-6">
          <div class="d-flex h-100 mb-5">
            <div class="justify-content-center align-self-center">
              <h2>
                <strong>Delicious Food Menu,</strong>
                <br />in Your Gadget
              </h2>
              <p>Ayo Segera Pesan Makanannya</p>
              <router-link to="/foods" class="btn btn-lg btn-success">Pesan</router-link>
            </div>
          </div>
        </div>

        <div class="col-md-6">
          <img src="../assets/img/hero.png" width="100%" />
        </div>

      </div>
    </div>

    <!-- MOBILE -->
    <div class="d-sm-block d-md-none">
      <div class="row mt-4">

        <div class="col-md-6">
          <img src="../assets/img/hero.png" width="100%" />
        </div>

        <div class="col-md-6">
          <div class="d-flex h-100 mb-5">
            <div class="justify-content-center align-self-center">
              <h2>
                <strong>Delicious Food Menu,</strong>
                <br />in Your Gadget
              </h2>
              <p>Ayo Segera Pesan Makanannya</p>
              <router-link to="/" class="btn btn-lg btn-success">Pesan</router-link>
            </div>
          </div>
        </div>

      </div>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style>
</style>