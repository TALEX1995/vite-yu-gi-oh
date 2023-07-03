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
    <PokemonCard />
</template>