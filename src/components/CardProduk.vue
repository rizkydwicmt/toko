<template>
  <div class="card shadow card-product">
    <img :src="'../assets/img/produk/'+product.gambar" class="card-img-top" />
    <div class="card-body">
      <h5 class="card-title">{{product.nama}}</h5>
      <p
        class="card-text"
      >Rp. {{product.harga}}</p>
      <router-link class="btn btn-success" :to="'/foods/'+product.id"><b-icon-cart></b-icon-cart> pesan</router-link>
    </div>
  </div>
</template>

<script>
export default {
  name: "CardProduk",
  props: ["product"],
};
</script>

<style>
</style>