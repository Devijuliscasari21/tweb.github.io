<template>
  <div class="pesanan-sukses">
      <Navbar />
      <div class="container">
          <row class="justify-content-center mt-5">
              <div class="col text-center">
                  <img src="../assets/images/sukses.png" width="300"/>
                  <h2>Pesanan Sukses!!</h2>
                  <h4>Harap tunggu pesanan nya ya...</h4>
              </div>
          </row>
      </div>
  </div>
</template>

<script>
import Navbar from '@/components/Navbar.vue';

export default {
    name: "PesananSukses",
      components: {
        Navbar,
      },
    
}
</script>

<style>

</style>