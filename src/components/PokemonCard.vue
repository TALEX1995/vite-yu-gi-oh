<script>
export default {
    props: {
        pokemonImg: String,
        name: String,
        type1: String,
        type2: String,
        color: String,
        generation: Number,
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
    <div class="d-flex flex-column ms-5 justify-content-center" :class="color.toLowerCase()">
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

<style lang="scss" scoped>
@use '../assets/scss/vars' as *;

img {
    width: 300px;
    height: 300px;
}

span {
    font-size: 20px;
    font-weight: 600;
}

.red {
    color: $red;
}

.green {
    color: $green;
}

.blue {
    color: $blue;
}
</style>