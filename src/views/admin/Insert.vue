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
              <a class="nav-link" href="#">
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
          <span>Tambah Data Sertifikasi</span>
        </div>
        <div class="card-body">
          <form v-on:submit.prevent="onSubmit">
            <div class="row">
              <div class="col-md-6">
                <div class="form-group">
                  <label for="nama_sertifikasi">Nama Sertifikasi</label>
                  <input
                    type="text"
                    class="form-control"
                    id="nama_sertifikasi"
                    name="nama_sertifikasi"
                    v-model="form.nama_sertifikasi"
                    placeholder="masukkan nama sertifikasi"
                  />
                </div>
              </div>
              <div class="col-md-6">
                <div class="form-group">
                  <label for="dosen_pengampu">Dosen Pengampu</label>
                  <input
                    type="text"
                    class="form-control"
                    id="dosen_pengampu"
                    name="dosen_pengampu"
                    v-model="form.dosen_pengampu"
                    placeholder="masukkan nama dosen pengampu"
                  />
                </div>
              </div>
              <div class="col-md-6">
                <div class="form-group">
                  <label for="hari">Hari</label>
                  <input
                    type="text"
                    class="form-control"
                    id="hari"
                    name="hari"
                    v-model="form.hari"
                    placeholder="masukkan hari"
                  />
                </div>
              </div>
              <div class="col-md-6">
                <div class="form-group">
                  <label for="jam">Jam</label>
                  <input
                    type="text"
                    class="form-control"
                    id="jam"
                    name="jam"
                    v-model="form.jam"
                    placeholder="masukkan jam"
                  />
                </div>
              </div>
              <div class="col-md-6">
                <div class="form-group">
                  <label for="tanggal">Tanggal</label>
                  <input
                    type="date"
                    class="form-control"
                    id="tanggal"
                    name="tanggal"
                    v-model="form.tanggal"
                    placeholder="masukkan tanggal"
                  />
                </div>
              </div>
            </div>
            <input type="submit" class="btn btn-primary" value="Tambah"/>
          </form>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data() {
    return {
      form:{
        nama_sertifikasi: "",
        dosen_pengampu: "",
        hari: "",
        jam: "",
        tanggal: ""
      }
    };
  },
  methods: {
    onSubmit() {
      let data = JSON.stringify({ 'nama_sertifikasi': this.form.nama_sertifikasi, 'dosen_pengampu': this.form.dosen_pengampu, 'hari': this.form.hari, 'jam': this.form.jam, 'tanggal': this.form.tanggal});
      axios
        .post(
          "http://localhost/sertifikasi_api/sertifikasi/create.php", data, {
        headers: {
            'Content-Type': 'application/json',
        }
    }
        )
        .then(async res => {
          const data = await res;
          if (data.status == 200) {
            alert("Data Berhasil Dikirim")
            this.$router.push("read");
          }
        })
        .catch(err => {
          alert("Data Gagal Dikirim");
          console.log(err);
        });
    },
  },
};
</script>
<style lang="stylus" scoped></style>