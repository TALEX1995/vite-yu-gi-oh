<script>
export default {
    data: () => {
        return {
            value: ''
        }
    },
    props: {
        filteredArray: Array
    },

    emits: ['value'],

    methods: {

    },

}
</script>

<template>
    <select class="form-select w-50 m-3" aria-label="Default select example" @change="$emit('value', value)"
        v-model="value">
        <option v-for="option in filteredArray" :value="option">{{ option }}</option>
    </select>
</template>