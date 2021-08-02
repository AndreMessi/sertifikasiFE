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
    <section class="tampilan mt-2">
      <div class="jumbotron">
        <h1 style="text-align:center; font-weight:bold;">SELAMAT DATANG DI WEBSITE</h1>
        <br />
        <h5 style="text-align:center; font-weight:bold;">PENDAFTARAN SERTIFIKASI</h5>
        <br />
        <h5 style="text-align:center; font-weight:bold;">STMIK AKAKOM YOGYAKARTA</h5>
      </div>
    </section>
    <section class="footer mt-2">
      <div class="footer">
        <div class="bottom section-padding">
          <div class="container">
            <div class="row">
              <div class="col-md-12 text-center">
                <div class="copyright">
                  <p>
                    ©
                    <span>2021</span>
                    <a href="#" class="transition">STMIK AKAKOM YOGYAKARTA</a> All rights reserved.
                  </p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {};
</script>

<style>
.bloc_left_price {
  color: #c01508;
  text-align: center;
  font-weight: bold;
  font-size: 150%;
}
.category_block li:hover {
  background-color: #007bff;
}
.category_block li:hover a {
  color: #ffffff;
}
.category_block li a {
  color: #343a40;
}
.add_to_cart_block .price {
  color: #c01508;
  text-align: center;
  font-weight: bold;
  font-size: 200%;
  margin-bottom: 0;
}
.add_to_cart_block .price_discounted {
  color: #343a40;
  text-align: center;
  text-decoration: line-through;
  font-size: 140%;
}
.product_rassurance {
  padding: 10px;
  margin-top: 15px;
  background: #ffffff;
  border: 1px solid #6c757d;
  color: #6c757d;
}
.product_rassurance .list-inline {
  margin-bottom: 0;
  text-transform: uppercase;
  text-align: center;
}
.product_rassurance .list-inline li:hover {
  color: #343a40;
}
.reviews_product .fa-star {
  color: gold;
}
.pagination {
  margin-top: 20px;
}
a:hover {
  text-decoration: none;
}
.section-padding {
  padding: 60px 0;
}
.bottom {
  background-color: #0a1c2e;
}
.bottom .copyright {
  color: #e5e5e5;
  font-weight: 600;
}
.copyright a {
  color: #f2ff49;
  margin-left: 3px;
  padding-right: 3px;
}
.bottom p {
  margin-bottom: 0;
  line-height: 50px;
  font-size: 16px;
  font-weight: 400;
}
.copyright p span {
  color: #d1caca;
}
.bottom .copyright p,
.bottom .copyright a:hover {
  color: #6c6d83;
}
</style>