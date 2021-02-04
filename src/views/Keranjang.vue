<template>
  <div class="keranjang">
    <Navbar :updateKeranjang="keranjangs"/>
    <div class="container">
      <!-- Breadcrumbs -->
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
              <li class="breadcrumb-item active" aria-current="page">Keranjang</li>
            </ol>
          </nav>
        </div>
      </div>

      <div class="row">
        <div class="col">
          <h2>
            Keranjang
            <strong>Saya</strong>
          </h2>
          <div class="table-responsive mt-3">
            <table class="table">
              <thead>
                <tr>
                  <th scope="col">#</th>
                  <th scope="col" width="35%">Foto</th>
                  <th scope="col">Makanan</th>
                  <th scope="col">Keterangan</th>
                  <th scope="col">Jumlah</th>
                  <th scope="col">Harga</th>
                  <th scope="col">Total Harga</th>
                  <th scope="col">Hapus</th>
                </tr>
              </thead>
              <tbody>
                <tr v-for="(keranjang, index) in keranjangs" :key="keranjang.id">
                  <th>{{index+1}}</th>
                  <td>
                    <img
                      :src="'../assets/img/produk/'+keranjang.product.gambar"
                      class="img-fluid shadow"
                    />
                  </td>
                  <td>
                    <strong>{{keranjang.product.nama}}</strong>
                  </td>
                  <td>{{keranjang.keterangan ? keranjang.keterangan : '-'}}</td>
                  <td>{{keranjang.jumlah_pemesanan}}</td>
                  <td align="right">Rp. {{keranjang.product.harga}}</td>
                  <td align="right">
                    <strong>Rp. {{keranjang.jumlah_pemesanan*keranjang.product.harga}}</strong>
                  </td>
                  <td align="center" class="text-danger" @click="hapusKeranjang(keranjang.id)">
                    <b-icon-trash></b-icon-trash>
                  </td>
                </tr>

                <tr>
                  <td colspan="6" align="right">
                    <strong>Total Harga :</strong>
                  </td>
                  <td align="right">
                    <strong>Rp. {{totalHarga}}</strong>
                  </td>
                  <td></td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Navbar from "@/components/Navbar.vue";
import axios from "axios";

export default {
  name: "Keranjang",
  components: {
    Navbar,
  },
  data() {
    return {
      keranjangs: [],
    };
  },
  methods: {
    setKeranjang(data) {
      this.keranjangs = data;
    },
    hapusKeranjang(id) {
      axios
        .delete("http://127.0.0.1:3000/keranjangs/" + id)
        .then(() => {
          axios
            .get("http://127.0.0.1:3000/keranjangs")
            .then((response) => this.setKeranjang(response.data))
            .catch((error) => console.log("Gagal : ", error));

          this.$toast.error("Sukses Hapus Keranjang", {
            type: "error",
            position: "top-right",
            duration: 3000,
            dismissible: true,
          });
        })
        .catch((error) => console.log("Gagal : ", error));
    },
  },
  mounted() {
    axios
      .get("http://127.0.0.1:3000/keranjangs")
      .then((response) => this.setKeranjang(response.data))
      .catch((error) => console.log("Gagal : ", error));
  },
  computed: {
    totalHarga() {
      return this.keranjangs.reduce(
        (item, data) => item + data.product.harga * data.jumlah_pemesanan,
        0
      );
    },
  },
};
</script>

<style>
</style>