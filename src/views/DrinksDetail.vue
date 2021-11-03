<template>
  <div class="drinks-detail">
    <Navbar />
    <div class="container">
      <div class="row mt-5">
        <div class="col">
          <nav aria-label="breadcrumb">
            <ol class="breadcrumb">
              <li class="breadcrumb-item">
                <router-link to="/" class="text-dark">Home</router-link>
              </li>
              <li class="breadcrumb-item">
                <router-link to="/Drinks" class="text-dark">Drinks</router-link>
              </li>
              <li class="breadcrumb-item active" aria-current="page">
               Drink Order 
              </li>
            </ol>
          </nav>
        </div>
      </div>

      <div class="row mt-3">
        <div class="col-md-6">
          <img :src="'/assets/images/' + product.gambar" class="img-fluid shadow" />
        </div>
        <div class="col-md-6">
          <h2><strong>{{ product.nama }}</strong></h2>
          <hr>
          <h4>Harga : <strong>Rp. {{ product.harga }} </strong> </h4>

          <form class="mt-4" v-on:submit.prevent>
            <div class="form-group mt-4">
              <label for="jumlah_pemesanan">Jumlah Pesanan</label>
              <input type="number" class="form-control" v-model="pesan.jumlah_pemesanan"/>
            </div>

            <div class="form-group">
              <label for="keterangan">Keterangan</label>
              <textarea v-model="pesan.keterangan" class="form-control" placeholder="ektra milk, gula nya sedikit"></textarea>
            </div>

            <button type="submit" class="btn btn-success" @click="pemesanan">
              <b-icon-cart></b-icon-cart>Pesan</button> 
          </form>
        </div>
      </div>

    </div>
  </div>
</template>

<script>
import Navbar from '@/components/Navbar.vue';
import axios from "axios";

  export default {
    name: "DrinksDetail",
      components: {
        Navbar,
      },
    data() {
      return {
        product: {},
        pesan: {}
      };
    },
    methods: {
      setProduct(data) {
        this.product = data;
      },
      pemesanan() {
       if(this.pesan.jumlah_pemesanan) {
          this.pesan.products = this.product;
        axios
          .post("http://localhost:3000/keranjangs", this.pesan)
          .then(() => {
            this.$router.push({ path: "/keranjang"})
            console.log("Berhasil")
          })
          .catch((err) => console.log(err))
       } else {
          console.log("Berhasil")
          }
      },
    },

    mounted() {
      axios.get("http://localhost:3000/products/"+this.$route.params.id)
        .then((response) => this.setProduct(response.data))
        .catch((error) => console.log(error))
  }
};
</script>

<style>

</style>