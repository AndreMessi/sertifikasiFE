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
              <a class="nav-link" href="/admin/read">
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
          <span class="btn btn-primary">Daftar Peserta Yang Mendaftar Sertifikasi</span>
        </div>
        <div class="card-body">
          <table class="table table-bordered">
            <thead>
              <tr>
                <th>No</th>
                <th>Nim</th>
                <th>Nama Mahasiswa</th>
                <th>Jurusan</th>
                <th>Pilihan 1</th>
                <th>Pilihan2</th>
                <th>Pilihan3</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="(peserta, index) in pesertas" :key="peserta.id_mhs">
                <td>{{index+1}}</td>
                <td>{{peserta.nim}}</td>
                <td>{{peserta.nama}}</td>
                <td>{{peserta.jurusan}}</td>
                <td>{{peserta.pilihan1}}</td>
                <td>{{peserta.pilihan2}}</td>
                <td>{{peserta.pilihan3}}</td>
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
      pesertas :[]
    };
  },
  methods:{
    getPeserta(){
      axios.get('http://localhost/sertifikasi_api/mahasiswa/peserta.php')
      .then(res => {
        this.pesertas = res.data.body
      })
      .catch(err => {
          // handle error
          console.log(err);
      })
    },
  },
  mounted(){
    this.getPeserta()
  }

};
</script>

<style lang="">
  
</style>