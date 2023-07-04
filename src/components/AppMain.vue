<script>
import { store } from '../data/store.js';
import PokemonCard from './PokemonCard.vue';
import FilterSelect from './FilterSelect.vue';

export default {
    data() {
        return {
            store,
            pokemonType: [
                "Bug",
                "Dark",
                "Dragon",
                "Electric",
                "Fairy",
                "Fighting",
                "Fire",
                "Flying",
                "Ghost",
                "Grass",
                "Ground",
                "Ice",
                "Normal",
                "Poison",
                "Psychic",
                "Rock",
                "Steel",
                "Water"
            ]
        }
    },

    components: { PokemonCard, FilterSelect }
}
</script>

<template>
    <h3 class="m-3">Sceglio il tipo di pokemon:</h3>
    <FilterSelect :filtered-array="pokemonType" />
    <div v-if="store.isLoading" class="fs-1">LOADING ...</div>
    <div v-else class="row row-cols-2">
        <div v-for="{ imageUrl, name, type1, type2, color, generation, hp, atk, def } in store.pokemons" class="col d-flex">
            <PokemonCard :pokemonImg="imageUrl" :name="name" :type1="type1" :type2="type2" :color="color"
                :generation="generation" :hp="hp" :atk="atk" :def="def" />
        </div>
    </div>
</template>


