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
    <section class="content mt-2">
      <div class="card">
        <div class="card-header d-flex justify-content-between">
          <span>Daftar Sertifikasi</span>
        </div>
        <div class="card-body">
          <form v-on:submit.prevent="onSubmit">
            <div class="row">
              <div class="col-md-6">
                <div class="form-group">
                  <label for="nim">Nim Mahasiswa</label>
                  <input
                    type="text"
                    class="form-control"
                    id="nim"
                    name="nim"
                    v-model="form.nim"
                    placeholder="masukkan nim mahasiswa"
                    required
                  />
                </div>
              </div>
              <div class="col-md-6">
                <div class="form-group">
                  <label for="nama_mhs">Nama Mahasiswa</label>
                  <input
                    type="text"
                    class="form-control"
                    id="nama"
                    name="nama"
                    v-model="form.nama"
                    placeholder="masukkan nama mahasiswa"
                    required
                  />
                </div>
              </div>
              <div class="col-md-6">
                <div class="form-group">
                  <label for="jurusan">jurusan</label>
                  <input
                    type="text"
                    class="form-control"
                    id="flexCheckDefault"
                    name="jurusan"
                    v-model="form.jurusan"
                    placeholder="masukkan jurusan"
                    required  
                  />
                </div>
              </div>
              <div class="col-md-6">
                <div class="form-group">
                  <label for="centang">Pilih Sertifikasi</label>
                  <div class="form-check">
                    <input
                      class="form-check-input"
                      type="radio"
                      name="pilihan1"
                      id="pilihan1"
                      value="CCNA"
                      v-model="form.pilihan1"
                    />
                    <label class="form-check-label" for="ccna">CCNA</label>
                  </div>
                  <div class="form-check">
                    <input
                      class="form-check-input"
                      type="radio"
                      name="pilihan2"
                      id="pilihan2"
                      value="TEOFL"
                      v-model="form.pilihan2"
                    />
                    <label class="form-check-label" for="toefl">TOEFL</label>
                  </div>
                  <div class="form-check">
                    <input
                      class="form-check-input"
                      type="radio"
                      name="pilihan3"
                      id="pilihan3"
                      value="ORACLE"
                      v-model="form.pilihan3"
                    />
                    <label class="form-check-label" for="toefl">ORACLE</label>
                  </div>
                </div>
              </div>
            </div>
            <input type="submit" class="btn btn-primary" value="Daftar" />
          </form>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      form: {
        nim: "",
        nama: "",
        jurusan: "",
        pilihan1: "",
        pilihan2: "",
        pilihan3: ""
      }
    };
  },
  methods: {
    onSubmit() {
      let data = JSON.stringify({
        nim: this.form.nim,
        nama: this.form.nama,
        jurusan: this.form.jurusan,
        pilihan1: this.form.pilihan1,
        pilihan2: this.form.pilihan2,
        pilihan3: this.form.pilihan3
      });
      axios
        .post("http://localhost/sertifikasi_api/mahasiswa/daftar.php", data, {
          headers: {
            "Content-Type": "application/json"
          }
        })
        .then(async res => {
          const data = await res;
          if (data.status == 200) {
            alert("Daftar Sertifikasi Berhasil");
            this.$router.push("read");
          }
        })
        .catch(err => {
          alert("Daftar Sertifikasi Gagal");
          console.log(err);
        });
    }
  }
};
</script>
<style lang="stylus" scoped></style>