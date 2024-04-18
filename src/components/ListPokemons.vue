<script setup>
    const pokemon = defineProps([ "name", "urlBasePng" ])
</script>

<template>
    <div class="col-4 ">
        <div class="card mb-3 cardListPokemon">
            <p class="text-center">{{ pokemon.name }}</p>
            <img 
            :src="urlBasePng" 
            alt="..."
            height="90" 
            class="card-img-top p-2"/>
        </div>
    </div>
</template>

<style scoped>
    .cardListPokemon{
        background: radial-gradient(#56ca86, #074986);
        cursor: pointer;
    }
    .cardListPokemon:hover{
        
        background: radial-gradient(#17bd5c, #074986);
    }
    .cardListPokemon img:hover{
        padding: .1rem;
    }

</style>
