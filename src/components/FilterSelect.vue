<script>
export default {

    props: {
        filteredArray: Array
    }
}
</script>

<template>
    <select class="form-select w-50 m-3" aria-label="Default select example">
        <option selected>Nessuno</option>
        <option v-for="option in filteredArray" value="option">{{ option }}</option>
    </select>
</template>