<script>
import { store } from '../data/store.js';
import PokemonCard from './PokemonCard.vue';

export default {
    data() {
        return {
            store
        }
    },

    components: { PokemonCard }
}
</script>

<template>
    <div class="row row-cols-2">
        <div v-for="{ imageUrl, name, type1, type2, color, generation, hp, atk, def } in store.pokemons" class="col d-flex">
            <PokemonCard :pokemonImg="imageUrl" :name="name" :type1="type1" :type2="type2" :color="color"
                :generation="generation" :hp="hp" :atk="atk" :def="def" />
        </div>
    </div>
</template>


