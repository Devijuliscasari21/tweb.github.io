<template>
  <div class="home">
    <Navbar/>
    <div class="container">
      <Hero />

     <div class="row mt-5">
       <div class="col">
            <img src="../assets/images/note.png" width="100%"/>
        </div>

        <div class="col md-6">
            <div class="d-flex h-100">
                <div class="justify-content-center align-self-center">
                     <h2><strong>Cara</strong>         Order</h2>
                     <p><strong>1.</strong> Klik Pesan pada halaman utama</p>
                     <p><strong>2.</strong> Cari menu favorit mu, lalu klik Pesan untuk melanjutkan pemesanan </p>
                     <p><strong>3.</strong> Masukkan jumlah pesanan & lampirkan catatan jika ada </p>
                     <p><strong>4.</strong> Cek kembali pesanan, ketikkan nama pemesan dan nomor meja di form </p>
                     <p><strong>5.</strong> Proses pemesanan selesai, selamat menunggu pesanan. Happy Order</p>     
                </div>
            </div>
        </div>

        <br/><br/> <br/><br/>
    </div>

      <div class="row mt-4">
        <div class="col">
          <h3>Best<strong>Coffee</strong></h3>
        </div>
        <div class="col">
          <router-link to="/Drinks" class="btn btn-success float-right"><b-icon-eye></b-icon-eye>Lihat semua</router-link>
        </div>
      </div>


      <div class="row mb-4">
        <div class="col-md-4 mt-4" v-for="product in products" :key="product.id">
          <CardProduct :product="product"/>
        </div>
      </div>

   


    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import Navbar from '@/components/Navbar.vue';
import Hero from '@/components/Hero.vue';
import CardProduct from '@/components/CardProduct.vue';
import axios from "axios";


export default {
  name: 'Home',
  components: {
    Navbar,
    Hero,
    CardProduct
  },
  data() {
    return {
      products: []
    }
  },

  methods: {
    setProducts(data) {
      this.products = data
    }
  },

  mounted() {
    axios.get("http://localhost:3000/best-products")
      .then((response) => this.setProducts(response.data))
      .catch((error) => console.log(error))
  },
};
</script>
