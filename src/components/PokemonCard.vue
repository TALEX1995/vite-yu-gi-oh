<script>
export default {
    props: {
        pokemonImg: String,
        name: String,
        type1: String,
        type2: String,
        color: String,
        generation: String,
        hp: Number,
        atk: Number,
        def: Number
    }
}
</script>

<template>
    <div class="mt-3">
        <img :src="pokemonImg" alt="name">
    </div>
    <div class="d-flex flex-column ms-5 justify-content-center">
        <span>Nome Pokemon: {{ name }}</span>
        <span>Tipo 1: {{ type1 }}</span>
        <span>Tipo 2: {{ type2 }}</span>
        <span>Colore: {{ color }}</span>
        <span>Generazione: {{ generation }}</span>
        <span>HP: {{ hp }}</span>
        <span>Attacco: {{ atk }}</span>
        <span>Difesa: {{ def }}</span>
    </div>
</template>

<style scoped>
img {
    max-width: 350px;
    height: 350px;
}
</style>