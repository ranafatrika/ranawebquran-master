<script>
export default{
  name: "NavBar",
};
</script>

<template>
  <nav class="navbar navbar-dark bg-primary fixed-top">
    <div class="container-fluid">
      <div class="navbar-header">
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarTogglerDemo02" aria-controls="navbarTogglerDemo02" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
      </div>
      <a class="navbar-brand" href="#">MY AL-QURAN | by quran.com</a>
      <img src="../assets/alq.png" alt="" width="40" height="40">
      <div class="collapse navbar-collapse" id="navbarTogglerDemo02">
        <ul class="navbar-nav me-auto mb-2 mb-lg-0">
          <li class="nav-item">
            <Router-link class="nav-link" aria-current="page" to="/">Home</Router-link>
          </li>
          <li class="nav-item">
            <Router-link class="nav-link" to="/about">Contact me</Router-link>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>
<style>
.navbar-brand {
  text-align: center;
  font-family: "Comic Sans MS";
}
</style>

