<template>
  <div class="food-detail">
    <Navbar />
    <div class="container">

      <!-- Breadcrumbs   -->
      <div class="row mt-4">
        <div class="col">
          <nav aria-label="breadcrumb">
            <ol class="breadcrumb">
              <li class="breadcrumb-item">
                <router-link to="/" class="text-dark">Home</router-link>
              </li>
              <li class="breadcrumb-item">
                <router-link to="/foods" class="text-dark">Foods</router-link>
              </li>
              <li class="breadcrumb-item active" aria-current="page">Food Order</li>
            </ol>
          </nav>
        </div>
      </div>

      <div class="row mt-4">
        <div class="col-md-6">
          <img :src="'../assets/img/produk/'+product.gambar"  class="img-fluid shadow">
        </div>
        <div class="col-md-6">
          <h2><strong>{{ product.nama }}</strong></h2>
          <hr>
          <h4>Harga: <strong>{{ product.harga }}</strong></h4>
          <form>
            <div class="form-group">
              <label for="jumlah_pemesanan">Jumlah Pesan</label>
              <input type="number" class="form-control" />
            </div>
            <div class="form-group">
              <label for="keterangan">Jumlah Pesan</label>
              <textarea class="form-control" placeholder="Keterangan"></textarea>
            </div>

            <button type="submit" class="btn btn-success float-right"><b-icon-cart></b-icon-cart> Pesan</button>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Navbar from "@/components/Navbar.vue";
import axios from "axios";

export default {
  name: "FoodDetail",
  components: {
    Navbar,
  },
  data(){
    return {
      product: {}
    }
  },
  methods: {
    setProduct(data){
      this.product = data
    }
  },
  mounted() {
    axios
      .get("http://127.0.0.1:3000/products/"+this.$route.params.id)
      .then((response) => this.setProduct(response.data))
      .catch((error) => console.log("Gagal : ", error));
  }
};
</script>

<style>
</style>