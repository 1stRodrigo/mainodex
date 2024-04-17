<script setup>
    const pokemon = defineProps([ "name", "urlBasePng" ])
</script>

<template>
    <div class="col-4">
        <div class="card mb-3">
            <p class="text-center">{{ pokemon.name }}</p>
            <img 
            src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/25.png" 
            alt="..." 
            class="card-img-top"/>
        </div>
    </div>
</template>

<style>

</style>
