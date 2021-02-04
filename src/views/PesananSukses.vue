<template>
  <div class="pesanan-sukses">
    <Navbar />
    <div class="container">
      <div class="row justify-content-center mt-4">
        <div class="col text-center">
          <h2><strong>Sukses !!</strong></h2>
          <h4>Pesanan anda berhasil diproses <br> selamat menunggu</h4>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Navbar from "@/components/Navbar.vue";

export default {
  name: "PesananSukses",
  components: {
    Navbar,
  },
};
</script>

<style>
</style>