<template>
  <div class="container mt-2">
    <section class="menu">
      <nav class="navbar navbar-expand-lg navbar-dark bg-primary">
        <a class="navbar-brand" href="#">STMIK AKAKOM SERTIFIKASI</a>
        <button
          class="navbar-toggler"
          type="button"
          data-toggle="collapse"
          data-target="#navbarScroll"
          aria-controls="navbarScroll"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarScroll">
          <ul class="navbar-nav mr-auto my-2 my-lg-0 navbar-nav-scroll" style="max-height: 100px;">
            <li class="nav-item active">
              <a class="nav-link" href="#">
                Sertifikasi
                <span class="sr-only">(current)</span>
              </a>
            </li>
            <li class="nav-item active">
              <a class="nav-link" href="/admin/peserta">
                Peserta
                <span class="sr-only">(current)</span>
              </a>
            </li>
          </ul>
          <form class="d-flex">
            <a href="/" class="btn btn-danger" type="submit" style="margin:3px;">Logout</a>
          </form>
        </div>
      </nav>
    </section>
    <section class="content mt-2">
      <div class="card">
        <div class="card-header d-flex justify-content-between">
          <a href="/admin/insert" class="btn btn-primary mb-2">+ Tambah Sertifikasi</a>
        </div>
        <div class="card-body">
          <table class="table table-bordered">
            <thead>
              <tr>
                <th>No</th>
                <th>Nama Sertifikasi</th>
                <th>Dosen Pengampu</th>
                <th>Hari</th>
                <th>Jam</th>
                <th>Tanggal</th>
                <th>Action</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="(sertifikasi, index) in sertifikasis" :key="sertifikasi.id_sertifikasi">
                <td>{{index+1}}</td>
                <td>{{sertifikasi.nama_sertifikasi}}</td>
                <td>{{sertifikasi.dosen_pengampu}}</td>
                <td>{{sertifikasi.hari}}</td>
                <td>{{sertifikasi.jam}}</td>
                <td>{{sertifikasi.tanggal}}</td>
                <td>
                  <router-link
                    :to="{ name: 'Update', params: {id_sertifikasi: sertifikasi.id_sertifikasi, nama_sertifikasi: sertifikasi.nama_sertifikasi, dosen_pengampu: sertifikasi.dosen_pengampu, hari: sertifikasi.hari, jam: sertifikasi.jam, tanggal:sertifikasi.tanggal}}"
                    class="btn btn-success"
                  >Edit</router-link> | 
                  <button @click="deleteItem(sertifikasi.id_sertifikasi)" class="btn btn-danger">Delete</button>
                </td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "HelloWorld",
  props: {
    msg: String
  },
  data() {
    return {
      sertifikasis :[]
    };
  },
  methods:{
    getSertifikasi(){
      axios.get('http://localhost/sertifikasi_api/sertifikasi/read.php')
      .then(res => {
        this.sertifikasis = res.data.body
      })
      .catch(err => {
          // handle error
          console.log(err);
      })
    }, 
    deleteItem(id_sertifikasi) {
      axios.delete('http://localhost/sertifikasi_api/sertifikasi/delete.php?id_sertifikasi='+id_sertifikasi)
      .then(res => {
         if (res.status == 200) {
            alert("Data Berhasil Hapus")
            window.location.reload()
            this.$router.push("read");
          }
      })
      .catch(err => {
          // handle error
          console.log(err);
      })
    } 
  },
  mounted(){
    this.getSertifikasi()
  }

};
</script>

<style lang="stylus" scoped>

</style>