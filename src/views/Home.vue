<template>
  <div class="home">
    <Navbar />
    <div class="container">
      <Hero />

      <div class="row mt-4">
        <div class="col justify-content-center align-self-center">
          <h2>
            Best
            <strong>Foods</strong>
          </h2>
        </div>
        <div class="col justify-content-center align-self-center">
          <router-link to="/foods" class="btn btn-success float-right">
            <b-icon-eye></b-icon-eye> Lihat Semua
          </router-link>
        </div>
      </div>

      <div class="row mb-3">
        <div class="col-md-4 mt-4" v-for="product in products" :key="product.id">
          <CardProduk :product="product"/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import Navbar from "@/components/Navbar.vue";
import Hero from "@/components/Hero.vue";
import CardProduk from "@/components/CardProduk.vue";
import axios from "axios";

export default {
  name: "Home",
  components: {
    Navbar,
    Hero,
    CardProduk,
  },
  data() {
    return {
      products: [],
    };
  },
  methods: {
    setProduct(data) {
      this.products = data;
    },
  },
  mounted() {
    axios
      .get("http://127.0.0.1:3000/best-products")
      .then((response) => this.setProduct(response.data))
      .catch((error) => console.log('Gagal : ', error));
  },
};
</script>
