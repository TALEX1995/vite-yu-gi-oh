<script>
export default {
    data: () => {
        return {
            searchedTerm: '',
        }
    },

    props: {
        placeholder: String
    }
}
</script>

<template>
    <form class="w-50" @submit.prevent="$emit('form-submit', searchedTerm)">
        <div class="form-group">
            <label for="input-text">Inserisci il testo:</label>
            <input v-model.trim="searchedTerm" type="text" class="form-control" id="input-text" :placeholder="placeholder">
        </div>
    </form>
</template>