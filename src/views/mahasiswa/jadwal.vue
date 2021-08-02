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
              <a class="nav-link" href="/">
                Home
                <span class="sr-only">(current)</span>
              </a>
            </li>
            <li class="nav-item active">
              <a class="nav-link" href="/mahasiswa/daftar">
                Daftar Sertifikasi
                <span class="sr-only">(current)</span>
              </a>
            </li>
            <li class="nav-item active">
              <a class="nav-link" href="/mahasiswa/jadwal">
                Jadwal Sertifikasi
                <span class="sr-only">(current)</span>
              </a>
            </li>
          </ul>
          <form class="d-flex">
            <a href="/register" class="btn btn-danger" type="submit" style="margin:3px;">Daftar</a>
            <a href="/login" class="btn btn-warning" type="submit" style="margin:3px;">Masuk</a>
          </form>
        </div>
      </nav>
    </section>
    <section class="content">
      <div class="card">
        <div class="card-header d-flex justify-content-between">
          <span class="btn btn-primary">Jadwal Sertifikasi</span>
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
              </tr>
            </thead>
            <tbody>
              <tr v-for="(jadwal, index) in jadwals" :key="jadwal.id_sertifikasi">
                <td>{{index+1}}</td>
                <td>{{jadwal.nama_sertifikasi}}</td>
                <td>{{jadwal.dosen_pengampu}}</td>
                <td>{{jadwal.hari}}</td>
                <td>{{jadwal.jam}}</td>
                <td>{{jadwal.tanggal}}</td>
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
      jadwals :[]
    };
  },
  methods:{
    getJadwal(){
      axios.get('http://localhost/sertifikasi_api/sertifikasi/read.php')
      .then(res => {
        this.jadwals = res.data.body
      })
      .catch(err => {
          // handle error
          console.log(err);
      })
    },
  },
  mounted(){
    this.getJadwal()
  }

};
</script>

<style lang="">
</style>