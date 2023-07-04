<script>
export default {
    data: () => {
        return {
            searchedTerm: '',
        }
    },

    props: {
        placeholder: String
    },

}
</script>

<template>
    <form class="w-50" @submit.prevent>
        <div class="form-group">
            <label for="input-text">Inserisci il testo:</label>
            <input @keyup.enter="$emit('form-submit', searchedTerm), searchedTerm = ''" v-model.trim="searchedTerm"
                type="text" class="form-control" id="input-text" :placeholder="placeholder">
        </div>
    </form>
</template>