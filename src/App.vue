<script setup>
import {ref} from 'vue'
import { RouterView } from 'vue-router';

let num = ref (0)

</script>

<template>
    <nav class="navbar navbar-expand-lg bg-primary">
  <div class="container-fluid d-flex justify-content-between">
      
      <router-link class="navbar-brand" to="/">
          <img src="./assets/img/icons8-bullbasaur-48.png" alt="">Mainodex
      </router-link>

      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNavDropdown" aria-controls="navbarNavDropdown" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon bold"></span>
        </button>

    <div class="collapse navbar-collapse" id="navbarNavDropdown">
        <ul class="navbar-nav">
            <li class="nav-item">
                <a class="nav-link active" aria-current="page" href="#">Home</a>
            </li>
            <li class="nav-item">
                <a class="nav-link" href="#">Features</a>
            </li>
            <li class="nav-item">
                <a class="nav-link" href="#">Pricing</a>
            </li>
            <li class="nav-item dropdown">
                <a class="nav-link dropdown-toggle" href="#" role="button" data-bs-toggle="dropdown" aria-expanded="false">
                    Dropdown link
                </a>
                <ul class="dropdown-menu">
                    <li><a class="dropdown-item" href="#">Action</a></li>
                    <li><a class="dropdown-item" href="#">Another action</a></li>
                    <li><a class="dropdown-item" href="#">Something else here</a></li>
                </ul>
            </li>
        </ul>
    </div>
</div>

</nav>


    <!-- Content -->
    <div class="main">
        <router-view></router-view>
    </div>


    <footer class="bg-primary text-light">
        <div>Desenvolvido para
            <a class="" href="https://maino.com.br/" target="_blank">Maino</a> 
            {{ new Date().getFullYear() }}</div>
    </footer>
</template>

<style>
    footer{
        position: fixed;
        bottom: 0;
        width: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
        height: 50px;
    }
</style>

