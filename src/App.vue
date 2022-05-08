<template>
<nav class="navbar navbar-expand-lg navbar-light bg-light fixed-top" style="background-color: #DAE5D0;">
  <div class="container">
    <a class="navbar-brand" href="#">Al-Quran</a>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav me-auto mb-2 mb-lg-0">
        <li class="nav-item">
          <router-link class="nav-link active" aria-current="page" to="/">Home</router-link>
        </li>
        <li class="nav-item">
          <router-link class="nav-link" to="/about">About</router-link>
        </li>
      </ul>
    </div>
  </div>
</nav>
  <router-view/>
  <!-- Copyright -->
  <div class="text-center p-4 bg-secondary fixed-bottom">
    © 2022 Copyright:
    <a class="text-black" href="https://github.com/MrFunnyide">Aji Bayu Permadi</a>
  </div>
  <!-- Copyright -->
</template>
<style>
nav {
     background-image: url(../src/assets/bgOne.png);
     border-end-start-radius: 25px;
     border-end-end-radius: 25px;
}
</style>
