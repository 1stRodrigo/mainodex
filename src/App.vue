<script setup>
import {ref} from 'vue'
import { RouterView } from 'vue-router';

let num = ref (0)

</script>

<template>
    <!-- Navbar search -->
    <nav class="navbar navbar-dark bg-primary">
        <div class="container-fluid">
            <router-link class="navbar-brand" to="/">
                <img src="./assets/img/icons8-bullbasaur-48.png" alt="Logo">Mainodex
            </router-link>
                <form class="d-flex" role="search">
                    <input class="form-control me-2" type="search" placeholder="Buscar Pokemón" aria-label="Search">
                    <button class="btn btn-outline-success" type="submit">Buscar</button>
                </form>
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
        height: 56px;
    }
</style>

