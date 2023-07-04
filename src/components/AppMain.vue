<script>
import { store } from '../data/store.js';
import PokemonCard from './PokemonCard.vue';
import FilterSelect from './FilterSelect.vue';
import axios from 'axios';


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

    methods: {
        typeFilterPokemon(tipo) {
            axios.get(`https://41tyokboji.execute-api.eu-central-1.amazonaws.com/dev/api/v1/pokemons?eq[type1]=${tipo}`).then(res => {
                store.isLoading = true;
                store.pokemons = res.data.docs;
            }).catch(err => {
                console.log(err.message)
            }).then(() => {
                store.isLoading = false
            })
        }
    },

    components: { PokemonCard, FilterSelect }
}
</script>

<template>
    <h3 class="m-3">Sceglio il tipo di pokemon:</h3>
    <FilterSelect :filtered-array="pokemonType" @value="typeFilterPokemon" />
    <div v-if="store.isLoading" class="fs-1">LOADING ...</div>
    <div v-else class="row row-cols-2">
        <div v-for="{ imageUrl, name, type1, type2, color, generation, hp, atk, def } in store.pokemons" class="col d-flex">
            <PokemonCard :pokemonImg="imageUrl" :name="name" :type1="type1" :type2="type2" :color="color"
                :generation="generation" :hp="hp" :atk="atk" :def="def" />
        </div>
    </div>
</template>


