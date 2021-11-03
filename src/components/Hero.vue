<template>
    <div class="row mt-5">
        <div class="col md-6">
            <div class="d-flex h-100">
                <div class="justify-content-center align-self-center">
                     <h2><strong>Kopii terbaik</strong> <br> pilihan anda </h2>
                     <p>Temani hari mu dengan secangkir kopi</p>
                     <router-link
                        class="btn btn-lg btn-success" to="/Drinks">
                        Pesan
                        </router-link>
                </div>
            </div>
        </div>
        <div class="col">
            <img src="../assets/images/hero.png" width="750px"/>
        </div>
    </div>
  
</template>

<script>
export default {
    name: 'Hero'

}
</script>

<style>

</style>